So here, you have a key Vault and there is a master key in here. You can write policies to manage who has access to these keys and you could also do audit logs to see who is using these keys. Now, let's look at encryption process and decryption process in the context of object storage.

So let's say you have an object in an object storage bucket. 

* 1- You upload some plaintext data there. 

* 2-First thing the service does and you want to encrypt it. The encryption is actually on by default. You could bring your own keys. If you don't do that, we actually do the encryption by default. So this showing how the process actually works.So objects storage service calls the Vault service and it asks to generate a data key.

* 3- And the Vault service returns a data key as well as it returns the data key encrypted with a master key. So that's why you see those two boxes there.

* 4- And then the object storage takes those keys, that data key and it does the encryption with the plain text data key. And then it throws away the data key. But in the bucket, it keeps the encrypted object in the bucket. And it also keeps the encrypted data key with it. Right. So you will see why it keeps the encrypted data key.

* 5- When at the time of making a request to decrypt this data, the encrypted data key data and encrypted data key are stored as you see that in the bucket. 

* 6- So object storage now makes a request to the Vault and it sends that encrypted data key as part of the request. 

* 7- Vault looks at the encrypted data key. It knows the master key because it is stored inside the Vault. So it strips out the other portion and sends the data key back remember.This data key is the one which is used for encryption and decryption. Now, once you have the data, you could actually decrypt your plaintext data with this data key. 

So this is a bit more advanced for a foundational course. But hopefully, you get an idea of how the Vault works, how this envelop encryption, the two tiered encryption works, and why it is useful. Because it limits your blast radius and you don't have to do encryption again in case you rotate your keys.