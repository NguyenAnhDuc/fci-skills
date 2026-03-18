# BSS Skills - AI Skills for FPT Cloud BSS Team

Internal mono-repo chứa các Claude Code / OpenClaw skills cho team BSS Compute.

## Skills

| Skill | Mô tả | Status |
|-------|-------|--------|
| `docsmith` | AI documentation workflow (Doc → Code pipeline) | ✅ Active |

## Cài đặt

```
/plugin marketplace add https://github.com/NguyenAnhDuc/bss-skills.git
/plugin install docsmith@nguyenanhduc
```

## Thêm skill mới

1. Tạo folder: `plugins/<skill-name>/`
2. Tạo `SKILL.md` trong folder đó
3. Đăng ký trong `marketplace.json`
4. Commit + push

## Structure

```
bss-skills/
├── marketplace.json
├── README.md
└── plugins/
    └── docsmith/
        ├── SKILL.md
        ├── templates/
        └── ...
```
