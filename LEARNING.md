# Lesson 01 · Conversation evidence

AI-drafted task summary, not a transcript or grade. It may be public. Use actual
short quotes or labeled paraphrases, name any help supplied, and link actual
work. Leave missing contributions Pending. A learner can review, correct or
remove excerpts before publication; accuracy approval is not proof of learning.
Label role-play honestly rather than treating it as an actual learner response.

**Lesson:** STUDIO-001. **Available conversation context:** Local setup, classroom trial, request-path prediction, and live calculator observation.

## Classroom trial

Learner paraphrase: I entered 6, selected Subtract, and entered 7 on the
[classroom calculator](https://calc.mywebclass.org). The browser and API each
returned −1, and the page showed “Results match.” Both matched the expected
result for this subtraction example.

## Prediction

Learner paraphrase: DuckDNS resolves the calculator hostname to the DigitalOcean
server's public IP. The browser connects to Traefik over HTTPS on port 443.
Traefik matches the hostname and forwards the request over `hosting-web` to the
calculator container, whose response returns through Traefik to the browser.
The coach supplied a hint to start with DNS.

## Check interpretation

Coach-assisted interpretation adopted by the learner: The Ubuntu Studio job passed Black, Pylint, pytest, and both
real-image Chromium tests. The public launch check separately sent `6 × 7`,
expected `42`, and received HTTP `200` with `42`. That confirms the hosted API
returned the expected result for this input. My Chrome observation provides
separate evidence for the live browser. [Ubuntu CI run](https://github.com/Sathvik-Alla/my-server-studio/actions/runs/42279540486)

## Browser observation

Learner paraphrase: I opened my calculator in Chrome without an HTTPS certificate
warning. I entered 6, selected Multiply, and entered 7. The calculator displayed
42. [Hosted calculator](https://qa-is373-sathvik.duckdns.org)

## Keep decision

Coach-assisted decision adopted by the learner: Keep the deployment because the live calculator opened in Chrome
without a certificate warning and displayed `42` for `6 × 7`. The automated
launch checks also recorded trusted HTTPS and both existing containers unchanged.

## Review

The learner reviewed the classroom trial, request-path prediction, and browser
observation and approved those excerpts for publication as accurate. The learner
also reviewed, adopted, and approved the check interpretation and keep decision.

## AI work and next step

The coach verified the local clone and SSH origin, completed Windows setup, and
fixed the Studio CLI's Windows SSH transport. The learner reported a passing
read-only server check. [SPEC.md](SPEC.md) links the sanitized launch evidence
and passing Ubuntu CI. The coach helped draft the interpretation and keep decision.
