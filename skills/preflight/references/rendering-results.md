# Compact screenshot status panel and browser gallery

Always include the returned gallery_url in ordinary chat text as
[View screenshots](RETURNED_GALLERY_URL), including while captures are pending
and when the compact panel is visible.
The browser gallery is the main inspection view and remains usable when a host,
including a mobile host, does not render MCP Apps. Do not fabricate links.

Only start_email_rendering opens the compact MCP panel. Result reads are data-only
and do not mount another panel. The compact panel and browser gallery refresh
queued/running results automatically according to poll_after_seconds. The panel
continues independently of the assistant's response, stopping on terminal/stalled
results, access expiry, authorization errors or teardown, and pausing while hidden.
Its read-only Refresh action remains a fallback. A newly delivered tool result
also updates the same table. The panel honours retry_after when the host forwards
it; without retry guidance it preserves available links and waits for manual
Refresh. The browser gallery retains its existing polling and error behavior.
Viewing, refreshing and switching captures do not start tests or spend credits.

## Shared status indicators

Keep one table row per selected app and requested mode columns in light, dark,
forced_dark order. Resolve friendly names from list_email_clients. Retain returned
client IDs when names are unavailable. Do not invent client support.

| State | Panel and gallery | Static legend |
| --- | --- | --- |
| pending / no capture yet | Grey outline circle, labelled accessibly Queued | Grey circle |
| processing | Blue rotating arc, labelled Rendering | Static blue outline circle |
| complete with available link | Green check circle linking to the capture | Matching green check circle |
| mode not requested | Grey dash | Matching dash |
| failed, expired, unavailable or stalled | Distinct explanatory state | Explain the displayed state |

Queued and rendering panel cells have no visible state text; retain accessible
labels and tooltips. Use the same icon dimensions, stroke and colours throughout.
Only rendering capture indicators animate, respecting reduced motion. Legend
icons never animate.

A panel check opens the selected app and mode in the browser gallery. Gallery
navigation shows the status for the current mode, so a ready Light capture does
not imply Dark is ready. Mode buttons and preview placeholders use the shared
icons. Unfinished and failed captures remain selectable; completed captures can
be inspected while others finish. Preserve current selection and zoom on refresh.
Zoom and Open image require an available screenshot. Image-loading failures retain
a direct browser fallback without starting a replacement render.

## Chat responses and text-only fallback

After acceptance, acknowledge the request, include the gallery link, and report
actual credits charged. Do not duplicate the compact panel with Markdown tables
or poll just to narrate progress. Explain when a gallery link is unavailable.

For explicit status requests, retrieve the existing test and respect
poll_after_seconds. A text-only results snapshot may use readable states:
Queued, Rendering, Failed, Expired, and Unavailable. Use friendly app names,
localized mode headings and View for available links. Retain all requested pairs
and separate failures from successful captures. Do not invent percentages or
finish-time estimates.

Do not publish repeated loading tables or claim that a skill can edit already-sent
chat messages or control a host's native spinner. No new render is needed to fix
a display problem. A completed render does not mean compatibility passed and does
not run HTML QA.

Use the actual returned URLs. Individual screenshot gateways issue storage
redirects lasting at most sixty seconds; never copy the temporary storage URL
into chat instead of its gateway.

## Gallery access and privacy

Gallery links use share.preflight.qa and grant access to one run through a signed
bearer token bound to the viewing OAuth connection and organisation. Anyone with
the link can view it until access ends, without another login.

The deadline is seven days from original run creation or connection expiry,
whichever is earlier. Reissuing or refreshing a link cannot extend it. Connection
revocation, lost permission, content removal and retention can end access sooner.
Do not suggest another account, guessed IDs or automatic paid rerenders when
access fails. Do not expose tokens except as the intended user-facing result URL.

After delivering available captures and actual charges, an optional visual
comparison may still be offered according to screenshot-comparison.md. Respect
declined offers and requests to skip comparison. No comparison button or automated
comparison verdict is part of this UI.
