# PatientScribe for Grok Bot

PatientScribe is an iPhone app that records your medical appointments and turns them into summaries and a health record you keep on your own device and in your own iCloud. This plugin lets Grok Bot read that record so you can ask about it. Once you connect one, an assistant handles what it reads under its own terms: see [Privacy](#privacy) before you connect.

The plugin is offered in Grok Bot only, not in the Cursor editor. This repository holds only the plugin's manifest (`.cursor-plugin/plugin.json`), its MCP configuration (`mcp.json`), a logo, and the licence. The plugin points at PatientScribe's hosted server, `https://patientscribe.app/mcp/`. Nothing in it runs on your computer, and it contains no API key, token, or secret: you sign in on PatientScribe's own page when you connect.

## What you can ask

- "Using PatientScribe, what changed since my last visit?"
- "Using PatientScribe, help me prepare questions for my cardiology appointment."
- "Using PatientScribe, which medications am I taking now?"
- "Using PatientScribe, do my doctors disagree about anything?"

Name PatientScribe in your question, for example "Using PatientScribe, what happened at my most recent visit?" Without the name, an assistant sometimes answers from its own memory instead of your record. If you turned on more than one profile, say whose record you mean.

## What the assistant can read

For each profile you switch on in the app: the visit timeline (date, provider, specialty, and a short overview), the health details from each visit and their current status, short quoted excerpts that show where a detail came from, and places where your providers disagree.

It is read-only and cannot change anything in PatientScribe. It never receives full transcripts, recordings, or Medicare claims.

The complete list is under [Privacy](#privacy).

## Before you connect

1. If you do not have the PatientScribe iPhone app yet, sign up for the beta at [patientscribe.app/join](https://patientscribe.app/join/). If you already have it, start at step 2. The app is in beta through TestFlight and needs iOS 26.1 or later.
2. In the app, turn on iCloud Sync, open a profile you own, and turn on **Available to assistants you connect**. Sign in on Apple's page when it appears. After you sign in, Apple's page can stay blank for a few seconds. Wait for it to close by itself.
3. Add PatientScribe to Grok Bot (next section), sign in with the same Apple or Google account you use in the app, and approve.

Also:

- Apple Accounts that use Advanced Data Protection cannot connect yet.
- Adding PatientScribe may need a paid plan with the assistant.
- From the [Terms of Service](https://patientscribe.app/legal/terms.html), section 9: "You may make a profile available to an Assistant only if you have the authority to share that person's health information with a third party service, as described in Section 1."

The full walkthrough is in the PatientScribe user guide: [Connect an assistant](https://patientscribe.app/guide/user-guide.html#connect-an-assistant).

## Add PatientScribe to Grok Bot

Open **Connect apps** (on iPhone, tap your avatar at the top left, then **Connect apps**), search for PatientScribe, and add it. When Grok Bot asks you to **Authorize** or **Authenticate**, finish the PatientScribe sign-in in your browser.

## How sign-in works

1. A PatientScribe page opens. If it does not, select **Connect** next to PatientScribe.
2. Sign in with the same Apple or Google account you use in the PatientScribe app.
3. The page asks whether to allow the assistant to read your PatientScribe records and lists what it can read. For Grok Bot, the page also warns that every bot or agent on that account can read these records, including Team Bots that coworkers can use. Select **Approve**.

You are never asked to paste a key or token into the assistant. xAI's documentation for Grok Bot says: "OAuth tokens are held on Cursor's connector backend, and the Bot invokes tools without receiving them." ([Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps))

## Privacy

The binding text is PatientScribe's [Privacy Policy](https://patientscribe.app/legal/privacy.html) and [Terms of Service](https://patientscribe.app/legal/terms.html). The passages below are quoted from the Privacy Policy, from PatientScribe's [Data & Privacy](https://patientscribe.app/data-privacy/) page, and from the PatientScribe [user guide](https://patientscribe.app/guide/user-guide.html#connect-an-assistant).

### What the record holds

From the Privacy Policy, section 2:

> Connecting an Assistant is optional and off by default. Each profile you own has its own switch for it; profiles other people share with you do not. While a profile is switched on, the App keeps a summary record of that profile in your own iCloud (the “Assistant Record”) and updates it whenever the profile changes, without you doing anything. The Assistant Record contains:
>
> - the person's name, and whether the profile is your own;
> - the visit timeline, with each visit's date, provider, specialty, and overview;
> - the health details from each visit with their status at that visit, including any status you set and any appointment location or preparation notes from the visit;
> - the profile's current health details;
> - short excerpts from your transcripts that show where each detail came from;
> - any disagreements the App found between your providers; and
> - your time zone, the time the record was made, and a label naming which of your devices keeps it updated, made from the device type and the date the App was installed on it.
>
> It does not contain full transcripts, recordings, the profile's photo or date of birth, or Medicare Claims Data.

### How PatientScribe's server reads it

From the Privacy Policy, section 2:

> To let Assistants read the Assistant Record, you sign in to your Apple Account once, on Apple's own sign-in page inside the App on your iPhone. That sign-in gives our server a credential for your iCloud, which we keep encrypted. Apple does not let us limit that credential to the Assistant Record: it gives access to all of your PatientScribe data in iCloud, including your transcripts and any Medicare Claims Data, and allows both reading and changing it. Our server's code uses it only to find and read Assistant Records, and never changes anything in your iCloud. When an Assistant asks a question, our server reads the Assistant Record of the person the question is about, passes the Assistant only the part the question needs, and keeps no copy. Our server stores the credential and your connection records, but no health information. To keep the credential working, our server uses it to check in with iCloud every 20 minutes or so, without reading your health information.

> The Assistant Record is protected by Apple's standard iCloud encryption, not end-to-end encryption, which is what lets our server read it with your credential.

### What the assistant receives

From the Privacy Policy, section 3:

> When you ask a connected Assistant about a profile you switched on, we send that Assistant the parts of the Assistant Record it asks for so it can answer you. Unlike our service providers, an Assistant does not work for us: you choose to send it your information, and its provider (for example, OpenAI for ChatGPT or Anthropic for Claude) receives that information under its own terms and privacy policy, not ours. We do not control how an Assistant uses, stores, or shares what it receives. An Assistant may keep past conversations, including answers that drew on your record, after you disconnect or turn a profile off. Medicare Claims Data is never sent to an Assistant.

From the Data & Privacy page:

> With Grok Bot [...], a connection belongs to the whole account there: every bot or agent on it can read the summary, including Team Bots that coworkers can use.

### Ending access

From the user guide:

> Tap **Settings**, then **Connected assistants**. The screen lists each connected assistant and when it was last used. A Grok Bot connection is listed as **Grok Bot or Cursor**, because both sign in the same way.

From the Privacy Policy, section 5:

> Use Disconnect in the App to end Assistant access. It ends every Assistant connection at once and deletes the iCloud credential. It does not remove the Assistant Record from your iCloud; turning a profile's switch off does. If you instead remove PatientScribe from one Assistant, that Assistant's connection stops working within 30 days of its last use, and your other connections are unaffected. [...] Information an Assistant has already received stays with that Assistant under its own terms.

### Not medical advice

PatientScribe helps you keep track of your care. It is not a medical device and does not give medical advice. An assistant can still get things wrong. Check anything important against the visit itself, and leave medical decisions to you and your care team.

## Support

Email privacy@patientscribe.app.

## License

MIT. See [LICENSE](LICENSE).
