### RSA for MicroPython

## !WARNING experimental only

This project was forked from: https://github.com/adafruit/Adafruit_CircuitPython_RSA

And modified to run on MicroPython boards.

Tested on the Pico-W

## Install

After connecting to Wifi, in the MicroPython Interpreter:

```bash
>>> import mip
>>> mip.install("github:KipCrossing/micropython_rsa")
```

## Usage

### Encryption/Decryption

```python
from rsa.key import newkeys
from rsa.pkcs1 import encrypt, decrypt

(public_key, private_key) = newkeys(512)
message = message.encode("utf-8")
encrypted_message = encrypt(message, public_key)
decrypted_message = decrypt(encrypted_message, private_key)
print("Decrypted Message: ", decrypted_message.decode("utf-8"))
```

### Sign/Verify

```python
from rsa.key import newkeys
from rsa.pkcs1 import sign, verify

print("Generating keypair...")
(public_key, private_key) = newkeys(496)
message = "legit data"
hash_method = "SHA-256"
signature = sign(message, private_key, hash_method)
if verify(message, signature, public_key) != hash_method:
    raise ValueError(
        "Verification failed - signature does not match secret message sent!"
    )
else:
    print("Verification succeeded - signature matches secret message sent!")
```

## NO WARRANTY

```
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
