# Updated EventPilot: quick guide

## Changes in this version

The organizer dashboard now works with the attendee portal. Attendees can sign up, sign in, register, view their tickets and read announcements. Organizers can list attendees, publish announcements, check in tickets and record recommendation actions.

Review fixes included:

- Both frontends use the deployed server address instead of each visitor's localhost.
- QR, chart, Markdown and Swagger assets load from local files.
- Input validation and Swagger authentication documentation match the API.
- Attendee sessions survive a restart, expire after 24 hours and are revoked on logout.
- Registration counts include the manual baseline, and MySQL locking prevents two people taking the last place.
- Check-in is restricted to the selected event and succeeds only once, even under concurrent requests.
- Historical registration/confirmation/attendance totals respect the selected date.
- Loading errors, private browser storage and HTTP clipboard/camera limitations have visible fallbacks.
- Delhi demo presentation and mobile layout fixes from the previous version are retained.

## Open the deployed app

1. Open http://3.110.130.114:8080/ .
2. Paste the private organizer key into the sidebar and select **Unlock dashboard**.
3. Select an existing event. All earlier events are retained during an upgrade.
4. Open http://3.110.130.114:8080/attendee.html in a separate tab.
5. Use a fictional account to register and view its ticket.
6. Under **Attendee Operations**, publish an announcement or check in that ticket for its event.
7. Use http://3.110.130.114:8080/docs to study or test the APIs. Select **Authorize** and enter the appropriate organizer key or attendee bearer token.

## View an organization's key

Unlock the organizer dashboard with your private owner key and open **Organizations & Access**. Each organization has a masked access key and a **Show key** option. Create additional organizations there and assign events to them. Organization keys unlock only their own events. The existing owner key remains valid and can manage all organizations.

## Important details

- Do not put portal registration totals into manual metrics; the dashboard adds portal totals itself.
- The current public site uses HTTP. Camera scanning is disabled there; enter the ticket code or choose a QR image instead.
- No emails or SMS are sent. Announcements are displayed inside the attendee portal.
- Keep the organizer key and `.env` private. Use demo data for the current HTTP presentation.
- No existing EventPilot data is reset, and no other AWS application is part of this deployment.

See `README.md` for local setup, deployment paths, backups and test commands.
