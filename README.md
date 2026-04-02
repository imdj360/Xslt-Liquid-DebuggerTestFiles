# XSLT & DotLiquid Debugger — Test Files

Sample templates and input files for testing the **XSLT Debugger** and **DotLiquid Debugger** VS Code extensions targeting Azure Logic Apps Standard.

---

## Extensions Required

| Extension | Install |
| --------- | ------- |
| **XSLT Debugger** (macOS) | `code --install-extension xsltdebugger-darwin-darwin-arm64-x.x.x.vsix` |
| **XSLT Debugger** (Windows) | `code --install-extension xsltdebugger-windows-win32-x64-x.x.x.vsix` |
| **DotLiquid Debugger** | `code --install-extension dotliquid-debugger-x.x.x.vsix` |

---

## Repository Structure

```
TestXslt/
  compiled/       XSLT 1.0 stylesheets (compiled engine + inline C#)
  saxon/          XSLT 2.0 / 3.0 stylesheets (Saxon .NET engine)
  TestFiles/      XML input documents
  XJPathFiles/    XPath test files and JSON inputs

TestLiquid/
  json-to-json/   Liquid templates that output JSON
  json-to-xml/    Liquid templates that output XML
  json-to-html/   Liquid templates that output HTML
  json-to-text/   Liquid templates that output plain text

.vscode/
  launch.json     Ready-to-use F5 launch configs for all templates
```

---

## DotLiquid Templates

All templates target **DotLiquid 2.0.361** (Azure Logic Apps Standard). Each `.liquid` file has a paired `.liquid.json` input file in the same folder — the extension detects it automatically.

### json-to-json/

| Template | Description |
| -------- | ----------- |
| `invoice-flat.liquid` | Flatten a nested invoice structure. Computes line totals, VAT, grand total. |
| `sales-order-transform.liquid` | B2B sales order with coupon codes, SLA lookup, per-category subtotals, state tax, and order tier logic. |
| `person-transform.liquid` | Person/contact data reshape with conditional fields. |

### json-to-xml/

| Template | Description |
| -------- | ----------- |
| `order-to-xml.liquid` | Convert a purchase order JSON to XML for B2B / EDI integration. |
| `customer-to-xml.liquid` | Customer JSON to ERP XML import with account tier logic (STANDARD / SILVER / GOLD / PLATINUM), multi-address loop, and tag split. |

### json-to-html/

| Template | Description |
| -------- | ----------- |
| `email-notification.liquid` | Order confirmation HTML email with item table, discount/tax calculation, conditional shipping badge, and address block. |

### json-to-text/

| Template | Description |
| -------- | ----------- |
| `shipping-label.liquid` | Plain-text shipping label and packing slip with fragile flag aggregation, weight totals, and conditional service label. |

### Running a Liquid Template

1. Open this folder in VS Code
2. Open **Run and Debug** (`Ctrl+Shift+D` / `Cmd+Shift+D`)
3. Pick a **Liquid:** config from the dropdown
4. Press **F5** — the template opens with the preview panel automatically

Or open any `.liquid` file and press `Ctrl+Shift+L` to open the preview manually.

---

## XSLT Templates

### compiled/ — XSLT 1.0 (Compiled Engine)

| Stylesheet | Input XML | Description |
| ---------- | --------- | ----------- |
| `ShipmentConfv1.xslt` | `ShipmentConf.xml` | Shipment confirmation transform |
| `foreach-test.xslt` | `foreach-test.xml` | Loop and iteration testing |
| `step-into-test.xslt` | `step-into-test.xml` | Breakpoint and step-into testing |
| `sample-inline-cs.xslt` | `sample.xml` | Inline C# scripting via `msxsl:script` |
| `sample.xslt` | `sample.xml` | Basic transform sample |
| `VarLoggingV1.xslt` | `VarLogging.xml` | Variable capture and logging |
| `ns-mapping-sample.xslt` | `ShipmentConf_ns.xml` | Namespace mapping |

### saxon/ — XSLT 2.0 / 3.0 (Saxon .NET Engine)

| Stylesheet | Input XML | Description |
| ---------- | --------- | ----------- |
| `ShipmentConfv2.xslt` | `ShipmentConf.xml` | XSLT 2.0 shipment transform |
| `ShipmentConfv3.xslt` | `ShipmentConf.xml` | XSLT 3.0 shipment transform |
| `ShipmentConfv3-foreach.xslt` | `ShipmentConf.xml` | XSLT 3.0 with `xsl:for-each-group` |
| `AdvShipmentConfv2.xslt` | `ShipmentConf.xml` | Advanced XSLT 2.0 features |
| `AdvShipmentConfv3.xslt` | `ShipmentConf.xml` | Advanced XSLT 3.0 features |
| `step-into-test.xslt` | `step-into-test.xml` | Breakpoint and step-into (Saxon) |
| `foreach-test.xslt` | `foreach-test.xml` | Loop testing (Saxon) |
| `VarLoggingV1.xslt` | `VarLogging.xml` | Variable logging (Saxon) |
| `ns-mapping-sample.xslt` | `ShipmentConf_ns.xml` | Namespace mapping (Saxon) |

### Running an XSLT Template

1. Open this folder in VS Code
2. Open **Run and Debug** (`Ctrl+Shift+D`)
3. Pick an **XSLT:** config from the dropdown
4. Press **F5**

---

## Requirements

| Requirement | Version |
| ----------- | ------- |
| VS Code | 1.105 or later |
| .NET SDK | 8.0 or later |
