### Password Secrecy
Message 1 is encrypted with `pk(IdP)`.  
The intruder does not know `inv(pk(IdP))`, therefore the password remains secret.

---

### Authorization Token (`NA`) Secrecy
- Message 1 is encrypted for `IdP`.
- Message 2 is encrypted for `B`.
- Messages 3 and 4 carry the ticket encrypted for `B`.

The intruder does not know:
- `inv(pk(IdP))`
- `inv(pk(B))`

Therefore, `NA` remains secret.

---

### Photo Secrecy
Message 5 is encrypted for `P`.  
The intruder does not know `inv(pk(P))`, therefore the photos remain secret.

---

### Conclusion
According to the **Dolev–Yao model**, a passive observer learns nothing about:
- the password,
- the authorization details,
- or the photos.