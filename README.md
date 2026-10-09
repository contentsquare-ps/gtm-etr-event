# Contentsquare ETR Event Tag for GTM

A Google Tag Manager (web) community template that triggers an **ETR (Event Triggered Recording) event** in Contentsquare. When the tag fires, Contentsquare saves the visitor's recorded session, so you can capture and replay the sessions where a key moment happened, such as an error, a failed checkout or a specific click.

## How it works

The tag pushes a `trackEventTriggerRecording` command to the Contentsquare `_uxa` queue:

```js
_uxa.push(["trackEventTriggerRecording", "<prefix><event name>"]);
```

The prefix is set by the **ETR Event Type** field:

| ETR Event Type | Prefix | Effect |
|----------------|--------|--------|
| Session Level (default) | `@ETS@` | The ETR event applies to the whole session. |
| Page Level | `@ETP@` | The ETR event applies to the current page view only. |

If the event name is undefined or the event type is not recognised, nothing is pushed. The tag then completes without sending an event.

## Fields

| Field | Required | Description |
|-------|----------|-------------|
| ETR Event Name | Yes | Name of the ETR event to send (max 255 characters). It can be a GTM variable. |
| ETR Event Type | No | `Page Level` or `Session Level`. Defaults to `Session Level`. |

## Usage

1. Make sure the Contentsquare tag is installed on the site and loads before this tag fires, so `_uxa` is available.
2. Add this template to your GTM workspace (Templates → Tag Templates → Search Gallery, or import `template.tpl`).
3. Create a new tag from the template and enter an **ETR Event Name**. Choose an **ETR Event Type**.
4. Attach a trigger for the moment you want to record, such as an error event, a button click or a form submission.
5. Publish the container.

## Permissions

The template needs access to the global `_uxa` (read, write, execute), which is how it pushes commands to the Contentsquare tag. It needs no other permissions.

## Links

- [Contentsquare documentation](https://docs.contentsquare.com/en/web/)
- [Contentsquare](https://contentsquare.com/)

## License

Apache License 2.0. See [LICENSE](LICENSE).
