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

Pending.

## Browser observation

Learner paraphrase: I opened my calculator in Chrome without an HTTPS certificate
warning. I entered 6, selected Multiply, and entered 7. The calculator displayed
42. [Hosted calculator](https://qa-is373-sathvik.duckdns.org)

## Keep decision

Pending.

## Review

The learner reviewed the classroom trial, request-path prediction, and browser
observation and approved those excerpts for publication as accurate.

## AI work and next step

The coach verified the local clone and SSH origin, completed Windows setup, and
fixed the Studio CLI's Windows SSH transport. The learner reported a passing
read-only server check. The automated launch results are recorded separately in
[SPEC.md](SPEC.md). Next, review the sanitized launch evidence and run the
prepared checks.
