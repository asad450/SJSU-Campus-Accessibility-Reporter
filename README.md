# SJSU Campus Accessibility Reporter
Team Members:
Asad Qazi
Travis Ezell
Alex Nguyen
[Partner 2]
## Problem

Maria is an SJSU student who uses a wheelchair and needs clear, safe, accessible routes to get to class. Today, accessibility barriers around campus, such as blocked curb ramps, cracked sidewalks, dark walkways, and inaccessible entrances, may be visible or easy to describe, but they do not always become structured reports that staff can quickly route and act on. The exact failure point is that a student’s complaint or photo may not clearly identify the location, issue type, urgency, affected user, and responsible department.

This project connects to SDG 10: Reduced Inequalities and SDG 11: Sustainable Cities and Communities because inaccessible campus spaces create unequal access for students with disabilities and make the campus less safe and inclusive.

## AI Capability

This system uses three AI capabilities from the labs. Structured data extraction turns a messy written complaint into consistent fields such as location, accessibility issue, affected user, urgency, responsible department, resident language, and recommended action. This fits the problem because campus staff need structured information before they can route or act on a report.

Image recognition analyzes a photo of a visible accessibility barrier, such as a cracked sidewalk or blocked ramp, and identifies the problem, who may be affected, urgency, and recommended response. Text generation then turns the structured report into a short acknowledgment for the student and a work-order summary for staff.

## Workflow

Input: A student submits a written complaint, a photo of the barrier, or both. Examples include a blocked curb ramp, cracked sidewalk, broken light, or blocked entrance.

AI processing: Gemini extracts structured fields from the written report, analyzes any uploaded image, rates urgency, recommends a department, and drafts a student acknowledgment and staff work-order summary.

Output: The system produces a structured report, a student-facing message, and a staff-facing summary.

Real-world action: A human reviewer from SJSU Facilities, Accessibility Services, Campus Safety, or City Public Works reviews medium/high urgency cases before routing or creating a work order.

Screenshots of prototype output are included in this repository:
- Lab 2 structured extraction output
- Lab 1 generated student and staff messages
- Lab 3 visual recognition output
- Edge case failure output

## Failure Case

One failure case came from the edge case test. The user said they use a wheelchair and reported a cracked, dark sidewalk near a bus stop across from the edge of SJSU. They also said they did not know whether the sidewalk belonged to SJSU or the city and did not know the street name.

The AI still assigned the responsible department as City Public Works. This is a failure because the system gave a confident routing decision even though the user explicitly stated that the jurisdiction was unclear. If the sidewalk actually belongs to SJSU, the report could be delayed or misrouted while the accessibility hazard remains unresolved.

## Oversight and Tradeoff

Human review should happen before routing any medium/high urgency accessibility issue or any report with unclear location, ownership, or department responsibility. The AI should support the decision by summarizing the issue and suggesting a department, but it should not replace human review when the report affects safe access to campus.

One change that would reduce harm is adding a jurisdiction uncertainty flag to the structured schema. If the user says they are unsure whether the issue belongs to SJSU or the city, the system should route the report to human review instead of choosing one department automatically. The tradeoff is that this slows down routing and requires more staff time, but it reduces the risk of urgent accessibility reports being sent to the wrong place.
