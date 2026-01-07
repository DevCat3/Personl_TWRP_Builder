# TWRP Recovery Builder

A streamlined GitHub Actions workflow for building customized Team Win Recovery Project (TWRP) images for Android devices.

---

## 🚀 Features

- 🎯 Automated Build Process - Build TWRP images with a single click
- 📱 Multiple TWRP Versions - Supports various TWRP versions (3.3.1 to 3.7.1)
- 🔧 Flexible Configuration - Works with different Android versions (9.0 to 12.1)
- 📦 Multiple Output Formats - Generates IMG, ZIP, and optional TAR for Samsung devices
- 🌐 GitHub Integration - Automatic releases with MD5 checksums and build metadata
- ⚡ Optimized Performance - Uses shallow clones and parallel processing

---

## 🛠️ Setup Instructions

1. Fork/Create Repository

1. Create a new GitHub repository or fork this one
2. Add your device tree to GitHub (if not already present)

2. Configure Workflow

No additional setup required! The workflow uses your GitHub automatically:
- Name: `DevCat3`
- Email: `omarelbakery2008@gmail.com`
- Username: `DevCat3`

(You can modify these in the workflow file if needed)

3. Required Secrets

This workflow uses the default `GITHUB_TOKEN` - no additional secrets required!

---

## 📋 How to Use

Running a Build

1. Go to your repository on GitHub
2. Navigate to Actions → TWRP Recovery Builder - Personalized
3. Click Run workflow
4. Fill in the form:
   - TWRP Version: Select from dropdown (e.g., `3.7.0_twrp-11.0`)
   - Device Tree: Your device tree URL
   - Device Tree Branch: Branch name (e.g., `android-11.0`)
   - Device Path: Path format (e.g., `device/samsung/gta4lve`)
   - Device Name: Device codename (e.g., `gta4lve`)
   - Build Target: `recovery`, `boot`, or `vendorboot`
   - (Optional) Create Samsung TAR: Check if building for Samsung device

5. Click Run workflow

Build Duration

- First build: 30-60 minutes (downloads 50GB source code)
- Subsequent builds: 15-30 minutes (uses cached sources)

---

## 📁 Required Device Tree Structure

Your device tree must contain one of these makefiles:

```
device/<brand>/<codename>/
├── twrp_<codename>.mk         # Preferred for AOSP-based TWRP
├── omni_<codename>.mk          # Alternative for older versions
└── AndroidProducts.mk         # Should reference the above
```

---

## 📤 Outputs

After successful build, the workflow creates a GitHub Release with:

File	Description	
`<target>.img`	The recovery/boot/vendor_boot image	
`recovery.zip`	ZIP containing the image file	
`<target>.tar`	(Samsung only) Odin-flashable TAR package	

Release Information Includes:
- TWRP Version & Android version
- Device tree commit hash
- MD5 checksum for verification
- Build date and device information

---

## 🔧 Configuration Options

TWRP Version Mapping

User Selection	Actual Manifest Branch	Android Version	
`3.7.1_twrp-12.1`	`twrp-12.1`	Android 12.1	
`3.7.0_twrp-11.0`	`twrp-11`	Android 11	
`3.6.2_twrp-11.0`	`twrp-11`	Android 11	
`3.6.1_twrp-10.0`	`twrp-10`	Android 10	
`3.5.x_twrp-9.0`	`twrp-9`	Android 9	

---

## ⚠️ Troubleshooting

Manifest Sync Error

If you see `couldn't find remote ref`, the branch name is incorrect. The workflow automatically maps:
- `twrp-11.0` → `twrp-11`
- `twrp-10.0` → `twrp-10`
- `twrp-9.0` → `twrp-9`

## Build Failures

- Missing Dependencies: Check `LDCHECK` path in device tree
- Python Errors: For Android 9-10, Python 2 is auto-installed
- Memory Issues: Build uses 24GB swap space by default

Permission Errors

Ensure your GitHub token has `contents: write` permission for releases.

---

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

---

## 📄 License

This workflow is provided as-is for building open-source TWRP recovery. TWRP is a trademark of Team Win LLC.

---

## 👤 Contact

- GitHub: [@DevCat3](https://github.com/DevCat3)
- Email: <omarelbakery2008@gmail.com>
- Telegram: [@CatDev3](t.me/CatDev3)
- Project: [Personal TWRP Builder](https://github.com/DevCat3/Personl_TWRP_Builder)

---

# 🙏 Credits

- [Team Win Recovery Project](https://twrp.me) - For the amazing recovery
- [minimal-manifest-twrp](https://github.com/minimal-manifest-twrp) - Clean manifest for building TWRP
- GitHub Actions Community - For the excellent automation tools

---

### Happy Building! 🎉
