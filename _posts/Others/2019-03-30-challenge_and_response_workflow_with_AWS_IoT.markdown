 In order to use your own X.509 certificates that have been signed by your CA certificate, AWS IoT first needs to verify that 
 you not only own the CA certificate but that you also have access to the private key for that certificate. The process of 
 validating ownership of a CA certificate is done through a  challenge and response workflow with AWS IoT.
 
 To verify ownership of the private key, you generate a
 - verification certificate using the CA certificate, 
 - the private key, 
 - and a registration code that you generate from AWS IoT.
 
 
