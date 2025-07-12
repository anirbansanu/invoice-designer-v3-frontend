I’m building a cutting-edge, full-featured **dynamic invoice and product label designer module** for my ERP system using **Laravel** (API backend) and **Vue 3 + Vite** (frontend). This will function as a **drag-and-drop, real-time editor** for business users to visually design **invoices, labels, packing slips, POS bills, shipping labels**, and more.

---

### 🎯 Goal

Enable non-technical users to:

- Design fully custom templates visually  
- Define layout and style of elements  
- Inject real-time data (customer/order/etc.)  
- Export to precise PDF or image formats  
- Share, version, and reuse templates  
- Scale the system for multi-tenant, SaaS-like use

---

### 🧩 Core Designable Components (Canvas Elements)

✅ Logo / Branding  
✅ Text Blocks  
✅ Company/Customer Info Blocks  
✅ Barcode (EAN-13, CODE128, UPC, etc.)  
✅ QR Code (dynamic from order/invoice URL, etc.)  
✅ Custom Variables (`{{invoice.number}}`, `{{customer.name}}`, etc.)  
✅ Item Table / Dynamic Tables  
✅ Page Backgrounds / Headers / Footers  
✅ Uploaded Images (brand, icons, etc.)  
✅ Rectangles, Lines, Shapes  
✅ Stamps/Signatures (upload or base64)  
✅ Dynamic Seals (e.g. "PAID", "SHIPPED")  
✅ Layout Blocks (row, column, group)

---

### 🖌️ Style & Layout Editor (Right Sidebar)

Real-time editable style controls per element:

- Dimensions (Width/Height)  
- Position (X, Y), Rotation, Z-index  
- Fonts (Family, Size, Weight, Color, Line Height, Letter Spacing)  
- Text Alignment (left/center/right/justify)  
- Background Color/Image  
- Stroke (Border Color, Width, Style)  
- Padding / Margin  
- Opacity / Visibility Toggle  
- Lock/Unlock element  
- Snap to grid toggle  
- Responsive anchor points (for responsive resizing)

---

### 🧠 Dynamic Variable System

- Replace `{{invoice.number}}`, `{{business.logo}}`, `{{order.tracking_code}}` at render time  
- Support nested variables (e.g., `{{order.customer.email}}`)  
- Conditional logic for visibility (e.g., `if customer.gst_number exists`)  
- Variable autocompletion dropdown while typing  
- Fallback value support (e.g., `{{customer.name | 'N/A'}}`)

---

### 📂 Import / Export / Backup

- **Export to JSON** — backup full template with all properties  
- **Import from JSON** — load saved template  
- **Export to PDF (real data)** — WYSIWYG to precise PDF (A4, Label sizes, POS paper roll)  
- **Export to Image (preview thumbnails)**  
- **Bulk export labels (multiple rows)** based on order/invoice dataset  
- **Import design from other template or brand**

---

### 📐 Output Rendering Engine

- Merge saved template JSON with actual backend data  
- Generate pixel-perfect PDFs using `wkhtmltopdf`, `Snappy`, `DOMPDF`, or Puppeteer  
- Support multi-page rendering  
- Set bleed areas, safe margins, label gaps  
- Barcode & QR rendered server-side (fallback) or client-side  
- Custom DPI and paper size per template  
- Render preview exactly as PDF will print

---

### 🔁 Versioning, Collaboration, & Reuse

- Save versions with timestamp, rollback  
- Clone template with new name or category  
- Live collaboration (WebSockets or Echo)  
- Shareable templates (public or org-wide)  
- Tag/categorize templates (e.g., Retail Label, POS Receipt)

---

### 💼 Label-Specific Features

- **Multi-label per sheet** layout (e.g., 3×10 stickers per A4)  
- **Label roll printer mode** (auto flow content vertically)  
- **Position detection** for starting print on specific slot  
- **Barcode label printing** (auto-fill from product SKU list)  
- **Dynamic label rendering loop** (e.g., generate 100 product labels from SKU array)  
- Set label padding, gaps, columns, rows per page

---

### 📦 Basic UI Features

- Sidebar toolbox (drag elements to canvas)  
- Zoom In/Out, Pan, Reset  
- Snap to grid / show alignment lines  
- Context menu (copy, paste, duplicate, layer up/down)  
- Undo / Redo  
- Toggle preview mode  
- Keyboard shortcuts (Ctrl+S, Ctrl+Z, etc.)  
- Toast notifications for success/error  
- Autosave draft with debounce

---

### 🔐 Permissions & SaaS Readiness

- Multi-tenant support (business_id scoped)  
- User roles: Viewer / Editor / Admin  
- Templates scoped to user, team, or business  
- Template sharing: private, public, team  
- API token security for image access  
- Cloud storage support for images (S3, local, Wasabi)

---

### 📚 Template Types / Categories

- Invoice Template  
- Return Invoice  
- Shipping Label  
- Barcode Label  
- POS Receipt  
- Price Sticker  
- Packing Slip  
- Gate Pass / Waybill  
- Asset Tag

---

### ⚙️ Backend (Laravel)

- REST API for CRUD: Templates, Images, Versions  
- File upload controller (image/png/jpeg/svg/pdf)  
- PDF generation controller with real data injection  
- Template category/tag management  
- Export/import endpoints (JSON templates)  
- Image storage (local or cloud via Laravel Filesystem)  
- Queue support for long render jobs (label batches)

---

### 🧰 Frontend (Vue 3 + Konva.js)

- Canvas rendering using **Konva.js** (with layering, resizing, rotating)  
- Dynamic property binding for real-time updates  
- Pinia store to manage canvas, active template, selected object  
- Axios for API integration  
- Toolbox (drag components)  
- Style Panel (bind properties of selected object)  
- Zoom / pan / canvas navigation  
- Support multi-canvas pages (tabs or pagination UI)

---

### 🔍 What AI Should Help With:

- Data schema (template JSON, backend models)  
- Database choice (MySQL vs MongoDB, indexing for JSON columns)  
- Laravel API structure and routes  
- Vue architecture (state management, components)  
- How to inject data dynamically in design  
- How to keep canvas and PDF output consistent  
- Efficient template import/export logic  
- Multi-page rendering strategy  
- Print-safe rendering (margins, DPI)  
- Real-time sync (collab mode)  
- Template versioning best practices  
- Mobile UI responsiveness strategy  
- Performance optimization (for 1000+ labels)

---

### 🧪 Final Request

✅ I want you to **generate the full Laravel + Vue 3 + Konva.js application source code**, implementing as much of the above as possible. The code should be organized, modular, and production-ready.

Provide the entire source code as a downloadable ZIP (Laravel backend + Vue frontend integrated). Use Vite, Tailwind/Bootstrap, and recommend any setup steps or `.env` variables if needed.

