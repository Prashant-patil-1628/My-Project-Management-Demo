# Project notes for Claude

## LinkedIn skills

The 12 LinkedIn marketing skills from
[sergebulaev/linkedin-skills](https://github.com/sergebulaev/linkedin-skills)
(MIT, upstream commit `8f8bc4b`) are vendored in `vendor/linkedin-skills/`.
`.claude/skills/linkedin-*` are symlinks into `vendor/linkedin-skills/skills/`.

- **Bundle root is `vendor/linkedin-skills/`.** Resolve relative paths in a
  skill's SKILL.md (`../../references/...`, `scripts/...`) against the real
  skill folder under `vendor/linkedin-skills/skills/`, not `.claude/skills/`.
- **Python helpers** (`lib.publish`, `lib.ApifyClient`, `lib.url_parser`, ...)
  are imported from the bundle root: run them with
  `cd vendor/linkedin-skills && python3 -c "import lib; ..."`.
  Dependencies: `pip install -r vendor/linkedin-skills/requirements.txt`.
- **API keys are optional.** Without them the skills draft text for the user to
  paste. Keys (`APIFY_TOKEN`, `PUBLORA_API_KEY`, `LINKEDIN_PLATFORM_ID`,
  `PIXFARO_TOKEN`) go in `vendor/linkedin-skills/.env` (see `.env.example`),
  which is git-ignored. Never commit them.
- Nothing is published to LinkedIn without the user's explicit approval of the
  draft.
- To update: re-copy `skills/ references/ lib/ scripts/` and the root docs from
  upstream into `vendor/linkedin-skills/` and update the commit hash above.
