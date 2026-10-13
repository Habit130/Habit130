# Build and Verification

The product is the English `README.md`, equivalent `README.zh-CN.md`, and
self-contained static SVG headers in `assets/profile/`.
No product build, lint, test, packaging, deployment, or CI command is configured.
Do not invent package scripts or treat unavailable checks as passed.

## Required order

1. Refresh the issue/comments and baseline; inspect changed files, project
    README references, links, paths, prose equivalence, and contract scope.
   For approved description deliveries, snapshot public metadata/control
   descriptions, branch-protection summaries and pin order before changes.
2. Run whitespace, governance structure, and static profile/SVG checks.
3. Verify ignore behavior. For explicitly approved description-only deliveries,
   re-read each field immediately before its own operation.
   Only the issue's observed-old value may be replaced; target means verified
   no-op, any third value pauses that operation. Use only the exact authorized
   description command, log exit/output and fresh readback, and compare unchanged
   settings/pins. Permission denial stops; no alternate endpoint or blind rollback.
4. Inspect actual rendered previews in both languages, at desktop and 375px,
   in light/dark modes, including GitHub branch README previews; check the
   light-image fallback, final diff, and live GitHub settings.
5. Check staged whitespace/scope; after commit and push, verify the exact PR
   head, status rollup, and delivery evidence. Follow the issue's command order.

Description edits publish immediately, independently of the README PR; record
before/after values and this timing in the PR/handback. Inspect actual public
cards separately from API readback and report cache delay honestly. A protected
branch flag alone does not establish every protection rule.

## Commands

| Task | Command | Evidence / notes |
| --- | --- | --- |
| Worktree status | `git status --short --branch` | Branch and existing changes |
| Whitespace | `git diff --check` | Before staging |
| Staged whitespace | `git diff --cached --check` | Before commit |
| Root instruction budget | `wc -l -c AGENTS.md` | Near 100 lines; below 12 KiB |
| Main sections | `grep -n '^## ' AGENTS.md` | Exactly six required sections |
| Ignore rules | `git check-ignore .local/agent-context.md docs/orchestration/handoffs/AC-0-v1-a1-execution.md` | Both ignored |
| Tracked README exceptions | `git check-ignore .local/README.md docs/orchestration/handoffs/README.md` | No output; exit 1 is expected |
| Final staged scope | `git diff --cached --stat` | Only confirmed artifacts |
| Final delivery diff | `git diff origin/main...HEAD` | Inspect after commit |

## Static profile/SVG check

Run from the repository root after both profile files and final assets exist.
This standard-library-only check verifies local links, nonempty image
alternatives, parseable SVGs, and the absence of active/external resources.

```sh
python3 - <<'PY'
from pathlib import Path
from urllib.parse import urlsplit, unquote
import re
import xml.etree.ElementTree as ET

root = Path.cwd().resolve()
def check_local(target):
    parsed = urlsplit(target)
    if parsed.scheme or parsed.netloc or not parsed.path:
        return
    path = (root / unquote(parsed.path).lstrip('/')).resolve()
    assert path == root or root in path.parents, target
    assert path.is_file(), target

for name, counterpart in [('README.md', 'README.zh-CN.md'),
                          ('README.zh-CN.md', 'README.md')]:
    text = (root / name).read_text()
    assert counterpart in text, f'{name}: missing language switch'
    for target in re.findall(r'!?\[[^\]]*\]\(([^)\s]+)', text):
        check_local(target)
    for target in re.findall(r'(?:src|srcset)="([^"]+)"', text):
        check_local(target)
    images = re.findall(r'<img\b[^>]*>', text)
    assert images and all(re.search(r'\balt="[^"]+"', image) for image in images), name

assets = list((root / 'assets/profile').glob('*.svg'))
assert assets, 'No final SVG assets'
banned = {'script', 'foreignObject', 'animate', 'animateMotion',
          'animateTransform', 'set', 'image', 'text'}
for path in assets:
    svg = ET.parse(path).getroot()
    assert svg.tag.rsplit('}', 1)[-1] == 'svg' and 'viewBox' in svg.attrib, path
    for element in svg.iter():
        assert element.tag.rsplit('}', 1)[-1] not in banned, path
        for key, value in element.attrib.items():
            key = key.rsplit('}', 1)[-1]
            assert not key.lower().startswith('on'), (path, key)
            if key == 'href':
                assert value.startswith('#'), (path, value)
    source = path.read_text()
    assert '@font-face' not in source and '@import' not in source, path
    for resource in re.findall(r'url\(\s*([^)]+)\)', source, flags=re.I):
        assert resource.strip().strip("'\"").startswith('#'), (path, resource)
print('PASS: profile files, local references, image alternatives, and static SVG checks')
PY
```

## Project-copy budget and semantics

For copy-polish deliveries, run the issue's standard-library budget/link block
after the unchanged static check above. Count only the three visible project
entries, including labels but excluding Markdown destinations/formatting;
the frozen issue supplies English-word/Chinese-character limits and exact links.
Preserve a readable baseline/final comparison and refresh public project README
sources (the reranking plugin uses `master`). Inspect bilingual meaning, project
order, experimental/in-progress status, CV workflow, upstream attribution and
the professional-diagnosis limitation separately; source docs are not runtime
or performance verification. Compare artwork/picture blocks with the baseline.

## Visual and semantic inspection

Static checks cannot establish original lettering, bilingual equivalence,
faithful personal/project claims, attribution, contrast, clipping, or layout.
Inspect those separately. For a new wordmark, provide three actual rendered
options and record habit's selection before finalizing the header.

Keep candidate sources, renderer/tooling outputs, and screenshots exclusively
in the allocated worktree's ignored `.local/profile-preview/` directory.
Use existing tools or isolated local tooling; record actual renderer, viewport,
mode, image-load/overflow results, and source revision. A GitHub Markdown API
preview is a useful local aid, not a replacement for the branch README view.
When the issue permits cached native rendering, preserve actual branch server
HTML and unmodified GitHub CSS with source URLs/digests and exact pushed head;
record renderer/settings, image/link/overflow measurements and baseline/new
mobile comparisons. Qualify offline/dynamic-chrome limits; old screenshots or
custom mockup CSS alone do not prove new branch presentation.
Do not start an unallocated server or silently treat unavailable rendering
as passed. No global software or product runtime is needed for this profile.

## Operational constraints

No dependency installation, network-link crawler, product build, or deployment
is required for the current baseline. Markdown local links are inspected
against repository paths; external links are not treated as guaranteed availability.

There are no configured machine-level shared resources.
Parse changed JSON and run `opencode debug config` only if a future delivery
changes runtime configuration. Update this guide when real executable paths appear.
