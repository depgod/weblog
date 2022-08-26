---
layout: post
title: Managing our GPG keys on linux for better security
---
## Tutorial


1. Create your own private/public key pair and revocation certificate
	```bash
	$ gpg --expert --full-gen-key	
	```
2. Export you public key
	```bash
	$ gpg --armor --export user-id > pubkey.asc
	```
3. Export your private key
	```bash
	$ gpg --export-secret-keys --armor user-id > privkey.asc
	```
4. Protect your priavte key and revocation certificate by keeping them somewhere safe.
5. List keys by signature:
	```bash
	$ gpg --list-sigs user_id
	```
6. List all keys:
	```bash
	$ gpg --list-keys user_id
	```
	
7. Share your public key on a public keyserver
	```bash
	$ gpg --send-key key_id
	```
	
	>**NOTE**: In Ubuntu by default all the keys are uploaded to keyserver.openpgp.com

8. Change default keyserver to another keyserver:
	```bash
	$ gpg [keyserver-address] --send-key key_id
	```
	
	>**NOTE**: If a public key is sent to OpenPGP, it sends a notification 
	on keyowners email address

9. By default keys are not available for search by email address, the mail
   from openpgp has a link inside it, which needs to be clicked to verify identity

10. After your key is verified, you can serach for your key on the keyserver:
	```bash
	$ gpg --search user_id
	```
	
11. Import others public key to your key-ring:
	>If you want to send someone an encrypted message you´ll first need to import
	their public key from a file or keyserver
	
	1. Import key from a file:
	```bash
	$ gpg --import public_key_file
	```

	2. Import if you already know a key_id:
	```bash
	$ gpg --recv-keys key_id
	```

	3. Import from a particular keyserver:
	```bash
	$ gpg --keyserver [keyserver-address] --recv-keys key_id
	```

12. Validate public keys:
	>When you recieve a public key from someone, once you imported that public key
	how would you verify that public key belongs to that person, we need to authenticate it.


	We can try following alternatives:
	1. You can view the fingerprint of the public key
	```bash
	$ gpg --fingerprint user_id
	```

	2. You can contact the keyś owner over the phone or meet in person.
	
	3. Compare the two fingerprints and if the two fingerprints match, means you have the right public key
	
	5. Then you sign the key as a valid key:
	```bash
	$ gpg --sign-key key_id
	```


13. Managing your keys

	1. List all keys
	```bash
	$ gpg --list-keys
	```

	2. List all keys with signature
	```bash
	$ gpg --list-sigs
	```

	3. Delete a key-id
	```bash
	$ gpg --delete_key key_id
	```

14. List keys in your private ring
	```bash
	$ gpg --list-secret-key
	```

15. How to extend key expiration date
	1. List all the keys
	```bash
	$ gpg --list-keys
	```
	
	2. Select a key using key-id which you want to change expiration of
	```bash
	$ gpg --edit-key key-id
	```
	
	3. Now you'll enter the gpg shell, here you can see all the applicable commands using `help`command
	```bash
	$ gpg> help
	```
	
	4. List all the keys and select a key you want to edit
	```bash
	$ gpg> list
	```
	
	5. Now enter  `expire` in the gpg shell to start editing the expiration date
	```bash
	$ gpg> expire
	Changing expiration time for the primary key.
	Please specify how long the key should be valid.
			 0 = key does not expire
		  <n>  = key expires in n days
		  <n>w = key expires in n weeks
		  <n>m = key expires in n months
		  <n>y = key expires in n years
	Key is valid for? (0)
	```
	
	6. Save the changes
	```bash
	$ gpg> save
	```

16. How to use the revocation certificate
	> If you're private key is compromised you can regenerate a new key pair using the revocation certificate to let everyone know that you are not using you're old key anymore.
	
	> On Linux their's a default revocation certificate stored in `~/.gnupg/openpgp-revocs.d/` location.

17. Following command should be used to revoke a key using a revocation certificate
	```bash
	$ gpg --output revocation.rev --gen-revoke key-id
	```
18. Now you should import it to your keyring
	```bash
	$ gpg --import revocation.rev
	```
19. Now upload the revoked key to the keyserver
	```bash
	$ gpg --send-key key-id
	```
	
