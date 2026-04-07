# Bug Bounty Write-ups

My public findings from bug bounty hunting. Real bugs, responsible disclosure.

### 1. 1xSlots Casino

**Date:** April 2026  
**Status:** Reported to the operator

**Findings:**
- No rate limit on login (`POST /api/internal/user/auth`)
- Telegram 2FA without rate limit (`POST /api/internal/socauth/two-factor-telegram`)
- Negative amounts in seam-wallet transfers
- Session IDOR (`closeSession`, `disconnectEverywhere`)
- Password reset endpoint returning 500
- Change withdrawal details without confirmation
- Disable 2FA without old code
- Any user can create giveaway

**Most critical:** login brute-force, 2FA bypass and balance manipulation.

[Read full write-up](https://bacdoor.github.io/writeup-1xslots.html)  

---

### 2. ON-X Casino

**Date:** April 2026  
**Severity:** Critical / High  
**Status:** Resolved, paid

**Findings:**
- KYC upload without authentication (`uploadVerificationDocuments`)
- `makeRebill` without auth guard
- Payout IDOR (`cancelPayout`)
- Bonus balance IDOR (activate / reset)
- `retryPaymentUrl` IDOR + missing auth
- Negative loyalty points exchange + race conditions
- Multiple mutation races (`rebill`, `bonusStoreBuyProduct`, etc.)
- WebSocket `connection_ack` without token

**Impact:** KYC sabotage, payout abuse, bonus manipulation, payment races.

[Read full write-up](https://bacdoor.github.io/writeup-onx.html)

---

### Pending Reports (handed to operator)

**Zooma Casino**  
2026 · Handed to the operator · Full details within 14 days

**BC.GAME**  
2026 · Handed to the operator · Full details within 14 days

**JetTon Casino**  
2026 · Handed to the operator · Full details within 14 days

**Shuffle**  
2026 · Handed to the operator · Full details within 14 days

**Cloudbet**  
2026 · Handed to the operator · Full details within 14 days

---

All reports follow responsible disclosure.  
Detailed PoCs available upon request after remediation.

More write-ups coming soon.
