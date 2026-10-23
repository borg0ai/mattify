# RFC lifecycle setup belongs to host `/specify`

Mattify does not own a second RFC engine. The host-installed `specify` skill owns `.spec/` initialization, RFC files, validation, status transitions, and consistency checks. `setup-mattify` checks whether a repository is ready and delegates those operations to the host skill.

Skills may use issue trackers as intake evidence or discussion context, but tracker setup does not authorize product implementation. Project changes require an Approved RFC, and implementation skills must use that RFC as their scope authority.

This keeps one source of truth for RFC status and prevents issue labels or ticket states from becoming accidental approval signals.
