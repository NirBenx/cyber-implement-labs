# Threat Hunting

Start with `rule.id`, `rule.level`, `agent.name`, timestamp, decoder, and source. For Auditd, pivot on `data.audit.command`, `data.audit.exe`, `data.audit.auid`, `data.audit.uid`, `data.audit.euid`, `data.audit.cwd`, and `data.audit.key`. For FIM, pivot on `syscheck.path`, event type, hashes, ownership, and diff availability.

Ask whether the event decoded correctly, login identity differs from effective identity, activity forms a sequence, the command is expected administration, and recurrence is genuine rather than test noise. Preserve queries, timestamps, raw events, related alerts, and conclusions; sanitize all public artifacts.
