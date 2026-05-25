# Sample PRD Review Report

## 1. Overall Conclusion

The PRD is not ready for implementation. The core object model is understandable, but ownership overwrite, transfer side effects, disabled-device behavior, external billing failure handling, and permission boundaries are underspecified.

## 2. Business Understanding

| Type | Content |
|------|---------|
| Stated | The portal manages device registration, customer binding, ownership transfer, and disabling devices. |
| Inferred | A device should have at most one active customer binding at a time. |
| Missing | Binding lifecycle, audit history, billing sync status, and overwrite permission rules. |
| Question | Should an operator be allowed to overwrite an existing binding, or only an admin? |

## 3. Key Risks

| Risk | Impact | Priority | Recommendation |
|------|--------|----------|----------------|
| Binding overwrite is allowed without a defined permission boundary | Operators may accidentally reassign customer devices | Critical | Restrict overwrite to admins or define a separate permission |
| Billing system sync failure is not handled | Local ownership may differ from billing ownership | Critical | Add sync states, retries, and manual recovery |
| Disabled-device rules are incomplete | Disabled devices may still be bound or overwritten | Major | Define whether disabled devices can be viewed, rebound, unbound, or re-enabled |

## 4. Detailed Findings

| ID | Severity | Type | Module | Finding | Recommendation |
|----|----------|------|--------|---------|----------------|
| BR-CR-001 | Critical | Permission gap | Customer Binding | Operators can overwrite existing bindings, but overwrite is a high-risk ownership operation. | Define an explicit `device-binding-overwrite` permission and log every overwrite. |
| BR-CR-002 | Critical | Exception gap | Ownership Transfer | The external billing system update has no failure path. | Add `pending_sync`, `sync_failed`, and `sync_success` states with retry and manual repair. |
| BR-MJ-003 | Major | State gap | Disable Device | The PRD only says disabled devices cannot be transferred. It does not define registration, binding, overwrite, or re-enable behavior. | Add a device status matrix by operation. |

## 5. Suggested PRD Wording

```text
Device binding overwrite:
- Only users with the device-binding-overwrite permission can replace an existing customer binding.
- Before overwrite, the system displays the current customer, new customer, device SN, and impact warning.
- After overwrite, the system records an audit log containing operator, timestamp, old customer, new customer, and reason.
```

```text
Billing sync:
- Ownership transfer creates a billing sync task.
- Transfer status values are pending_sync, sync_success, sync_failed, and manual_review.
- If billing sync fails, local ownership remains updated but the device detail page displays sync_failed and allows authorized retry.
```

## 6. Questions For Product

| ID | Question | Impact |
|----|----------|--------|
| Q-001 | Can operators overwrite existing customer bindings, or is admin approval required? | Determines permission and audit design. |
| Q-002 | Should local ownership update be rolled back if billing sync fails? | Determines transaction and recovery strategy. |

