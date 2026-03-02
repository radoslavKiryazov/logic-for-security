```mermaid
sequenceDiagram
    participant A as (A) User
    participant I as Intruder (i) [Role P]
    participant B as (B) Resource Server

    Note over I: IK = {a, b, i, id, pk(a), pk(b), pk(i), pk(id), inv(pk(i))}

    A->>I: TicketB
    Note over I: IK = IK ∪ {TicketB} <br/> (Intruder cannot read it, but stores it as a constant)

    I->>B: {i, b, np, TicketB}inv(pk(i))
    Note over I: Solve IK ⊢ Message 4 <br/> via Compose(i, b, np, TicketB) <br/> using inv(pk(i))

    B->>I: {{b, i, np, Photos}inv(pk(b))}pk(i)
    Note over I: IK = IK ∪ {M5} <br/> Analyze via DecAsym using inv(pk(i)) <br/> Result: {b, i, np, Photos}inv(pk(b)) 
    Note over I: IK = IK ∪ {Photos} <br/> (Photos extracted from decrypted block)
    
    Note over I: Role P Successfully Executed - Photos Leaked!
