# softwaresubject
sequenceDiagram
    participant User
    participant CartSystem
    participant PaymentGateway
    participant OrderSystem

    User->>CartSystem: add_item(item_id=123)
    activate CartSystem
    CartSystem-->>User: cart_updated(total_items=3)
    deactivate CartSystem

    User->>CartSystem: checkout()
    activate CartSystem
    CartSystem->>PaymentGateway: process_payment(amount=55000)
    activate PaymentGateway
    PaymentGateway-->>CartSystem: payment_status=SUCCESS
    deactivate PaymentGateway
    CartSystem->>OrderSystem: create_order(items=[123])
    activate OrderSystem
    OrderSystem-->>CartSystem: order_id=789
    deactivate OrderSystem
    CartSystem-->>User: order_confirmed(order_id=789)
    deactivate CartSystem
