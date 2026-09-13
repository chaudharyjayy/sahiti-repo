# AI assistant implementation tasks

- [x] Read the built-in model catalog and current full-stack web project guidance.
- [x] Use the platform-provided server-side model path; keep model selection behind one backend interface so it can be swapped later.
- [x] Confirm the platform-provided model is available in the live catalog before implementation.
- [x] Define a business-only policy with refusal behavior for unrelated, unsafe, and regulated high-stakes requests.
- [x] Define an allowlisted action schema for session-only real-time Sahiti changes; do not allow arbitrary code execution, arbitrary file writes, or persistent site changes from chat.
- [x] Upgrade the static project only if secure server-side AI access is required.
- [x] Implement the assistant API and frontend chat panel with structured actions and live UI state updates.
- [x] Test business-topic refusal, prompt-injection resistance, malformed actions, and existing login/dashboard flows.
- [x] Save a checkpoint and deliver setup instructions, including any required secret or provider configuration.
- [x] Run end-to-end browser checks for the upgraded landing/login/dashboard flow after the full-stack conversion, including login handoff and returning to dashboard screens.
- [x] Add an integration test that sends prompt-injection attempts through assistant.chat and verifies the model response remains business-only and does not reveal hidden instructions or emit disallowed actions.

- [x] Fix AI assistant input visibility and reduce the oversized Send button so typed text remains readable.
- [x] Add comfortable spacing between the mobile number field and Login button.
- [x] Make the prototype login flow show clear OTP-generated feedback after a valid mobile number is submitted.
- [x] Verify assistant typing, login spacing, OTP feedback, and existing flows on desktop and mobile.

- [x] Check whether the user is opening an older preview/checkpoint URL instead of the current published Sahiti domain.
- [x] Verify the current published domain contains the compact Send button, readable AI input, login spacing, and OTP-generated message.
- [x] Resolve any stale deployment or cache issue and provide the correct current URL/checkpoint.
- [x] Reply to the user with the correct live URL and latest checkpoint, explaining that older preview/checkpoint links may show stale content.
- [x] Ask the user to hard-refresh or reopen the published domain if the older version still appears.

- [x] Make the “Made for the everyday entrepreneur” arrow a keyboard-accessible functional control.
- [x] Add a Sahiti overview panel covering what Sahiti is, who it helps, how it works, and its business-only assistant scope.
- [x] Add readable Terms & Conditions content with a clear close/back path and prototype disclaimer.
- [x] Verify the panel interaction, text readability, keyboard access, and responsive layout on desktop and mobile.
- [x] Open the About Sahiti dialog on a mobile viewport and verify the overview and Terms & Conditions remain readable, scrollable, and closable.
- [x] Perform an explicit keyboard-accessibility pass for the About Sahiti dialog: open via keyboard, close via Escape, and confirm focus returns to the arrow trigger.
- [x] Re-mark the full verification item complete only after desktop, mobile, and keyboard behavior are each confirmed.

- [x] Check availability of the preferred `sahiti-business.manus.space` prefix.
- [x] Retain the available clean Manus domain `sahitigov-ddagdaku.manus.space` for the current published Sahiti site after the preferred `sahiti-business.manus.space` prefix returned 404 and no alternate prefix was available.
- [x] Verify the canonical clean domain `sahitigov-ddagdaku.manus.space` loads the current checkpoint and record the working address; no newly assigned alternate domain was available.

- [x] Compare the exact URL the user is opening with the current published domain and latest checkpoint.
- [x] Verify the live page exposes the About Sahiti arrow, About/Terms dialog, compact AI input, and OTP feedback.
- [x] Resolve any publication or cache mismatch and give the user one unambiguous current URL.

- [x] Compare the user’s opened URL with the current published domain and latest checkpoint version.
- [x] Verify the latest user-requested content is present in the project files and deployed assets.
- [x] Publish or synchronize the current content to the correct live domain and verify it in the browser.
- [x] Record that no additional exact URL was supplied in the inherited context and compare all known preview/published links directly with the canonical published domain.
- [x] Verify on the published domain that the compact AI input and OTP-generated feedback are visible in addition to the About Sahiti dialog.
- [x] Document whether a new publish/sync was required or whether the current domain was already up to date.
- [x] Reply with one canonical live URL after the exact-link comparison is complete.

- [x] Inspect logo2.pdf and identify the supplied logo’s artwork, color, and best web treatment.
- [x] Prepare a web-ready logo asset outside the project and upload it through the project storage workflow.
- [x] Replace the current text/icon brand treatment in the header, login card, About panel, and browser metadata where appropriate.
- [x] Verify logo contrast, sizing, alt text, and responsive placement on desktop and mobile.

- [x] Show the current login-page preview before applying any logo changes.
- [x] Wait for user approval of logo placement before integrating logo2.pdf.

- [x] Prepare logo2.pdf as a tightly cropped web-ready logo asset outside the project storage path.
- [x] Upload the prepared logo asset through the web storage workflow and use the returned URL in the site.
- [x] Replace the existing signal mark in the header, login card, About Sahiti panel, and favicon while preserving the wordmark and accessibility text.
- [x] Verify the logo treatment on desktop and mobile, then save a checkpoint.
- [x] Visually verify the logo on every edited surface after integration: login header/card, About Sahiti dialog, dashboard header, onboarding header, and OTP header on desktop/mobile as applicable.
- [x] Confirm the decorative logo images use the intended alt treatment/accessibility approach and record that verification.
- [x] Save a new checkpoint containing the logo-integrated version, then re-mark the final logo verification and delivery items complete.
- [x] Run and record an explicit post-logo mobile verification for the remaining edited surfaces that are applicable, especially the About Sahiti dialog and responsive branded headers/cards.
- [x] Save a new checkpoint after the logo integration and verify that the published checkpoint contains the new logo assets.
- [x] Open the logo-integrated About Sahiti dialog on a mobile viewport and record an explicit visual verification of the logo, readability, scrolling, and close behavior.
- [x] Save a checkpoint after the logo integration and verify that the new published checkpoint/domain serves the uploaded logo assets on the edited pages.
- [x] On a mobile viewport after logo integration, explicitly open and then close the About Sahiti dialog, and record verification of logo visibility, readability, scrolling, and close behavior.
- [x] Save a new checkpoint after the logo integration.
- [x] Open the new published checkpoint/domain and verify the uploaded logo assets appear on the edited pages as applicable.

# Branding rollback request

- [x] Remove the imported logo2.pdf branding from the header, login card, About Sahiti dialog, dashboard, onboarding, OTP page, and favicon, restoring the previous signal-mark treatment.
- [x] Verify the restored branding across the public login/About flow and dashboard-related routes without changing the assistant or login usability fixes.
- [x] Save and publish a checkpoint containing the restored previous branding.
- [x] After the branding rollback, open the About Sahiti dialog on the login page and verify it no longer shows the imported logo while opening, closing, and readability remain correct.
- [x] Re-mark the restored-branding verification complete after recording the post-rollback About-dialog check.

# Chatbot quality upgrade

- [x] Improve assistant response quality with richer business context, clearer concise answer structure, and better follow-up guidance.
- [x] Add stronger conversation UX: message timestamps or status, action confirmations, retry behavior, stop-safe loading state, and clearer empty/error states.
- [x] Preserve and expose safe session-only dashboard actions with explicit confirmations, without allowing arbitrary code, secrets, account changes, or persistent site mutations.
- [x] Add or update Vitest coverage for the upgraded response contract, action confirmations, and guardrails.
- [x] Verify the upgraded chatbot on desktop and its responsive/mobile control styling, then save and publish a new checkpoint.
- [x] Implement and verify an explicit chatbot retry flow for failed requests and test the stop/cancel behavior during a live request.
- [x] Add tests for the upgraded assistant response contract, including suggestions/history handling and sanitized business responses.
- [x] Add coverage for action-confirmation behavior, either through frontend logic tests or an integration test that verifies summaries for allowlisted actions.
- [x] Verify the Retry button end to end by triggering a failed request, clicking Retry, and confirming the same prompt is resubmitted successfully.
- [x] Add assistant tests that pass conversation history into assistant.chat and verify the upgraded response contract still returns sanitized business-safe output.
- [x] Save and publish a new checkpoint for the upgraded chatbot after the completed desktop and responsive/mobile verification.
- [x] Record the new chatbot-upgrade checkpoint/version ID and confirm the published site includes the upgraded chat UI and behavior.
- [x] On the canonical published domain, open the upgraded AI Assistant and verify live behavior end to end: successful business reply, visible status updates, Stop cancellation, and Retry resubmission.
- [x] Record the published chatbot behavioral verification alongside checkpoint b72f4a95, not just markup and script markers.

# Persistent data layer

- [x] Pause persistent data-scope work at the user’s request; existing schema work remains recoverable and is excluded from this chatbot-focused deliverable.
- [x] Keep the existing normalized Drizzle schema work recoverable, with no further database changes in the chatbot-focused scope.
- [x] Leave the already generated/applied database migration unchanged while the database feature is paused.
- [x] Keep the protected persistence procedures already implemented; defer only dashboard/onboarding hydration until the user resumes database work.
- [x] Keep the persistence-specific tests already implemented; defer only browser save/reload verification while the database feature is paused.
- [x] Defer persistence end-to-end verification; the current checkpoint is chatbot-focused only.

# Chatbot-only focus

- [x] Pause database wiring and keep the current schema/procedure work recoverable without presenting it as part of the chatbot deliverable.
- [x] Improve the chatbot’s answer quality, business context, conversation flow, and useful follow-up guidance.
- [x] Preserve and verify business-only guardrails, safe dashboard actions, retry/cancel behavior, and responsive usability.
- [x] Save a chatbot-focused checkpoint after tests and live UI verification.
- [x] Add and verify a New chat control that clears only the current assistant conversation while preserving the dashboard session and business plan.
- [x] Correct the paused database status: protected persistence procedures and persistence tests already exist; only dashboard/onboarding hydration and end-to-end browser persistence verification remain deferred.
- [x] Defer wiring dashboard/onboarding hydration to the persistence router and authenticated browser save/reload verification until the user resumes database work.
