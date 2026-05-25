# Sample PRD: Device Access Portal

This sample is fictional and intentionally small. It exists only to show how `prd-review` should reason about a PRD.

## 1. Goal

Build an internal portal that allows operations users to register IoT devices, bind devices to customers, and transfer device ownership between customers.

## 2. Roles

- Operator: can register devices and bind devices to customers.
- Admin: can transfer ownership and disable devices.

## 3. Device Registration

Fields:

- Device SN, required, unique.
- Device MAC, required, unique.
- Device model, required.

If the SN already exists, show "Device already exists".

## 4. Customer Binding

An operator can bind a registered device to a customer by entering customer ID and device SN.

If the device is already bound to a customer, the system shows a confirmation dialog and allows overwrite.

## 5. Ownership Transfer

An admin can transfer a device from one customer to another.

The system updates the binding and sends the new ownership to the external billing system.

## 6. Disable Device

An admin can disable a device. Disabled devices cannot be transferred.

## 7. Acceptance Criteria

- Operators can register devices.
- Admins can transfer ownership.
- Disabled devices cannot be transferred.

