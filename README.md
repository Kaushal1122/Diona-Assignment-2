# Criminal Risk Assessment Request

## Video Explanation

**Google Drive Video:** [Watch the project explanation](PASTE_GOOGLE_DRIVE_VIDEO_LINK_HERE)

> **Important:** Replace `PASTE_GOOGLE_DRIVE_VIDEO_LINK_HERE` with the actual Google Drive video link before submitting the repository.

---

## Project Overview

This repository contains the complete, production-ready implementation of the **Criminal Risk Assessment Request** form, structured according to official ODK (Open Data Kit) XLSForm standards and compiled into standard XForms XML.

The form digitizes the official intake and assessment workflow for the Province of Manitoba, capturing:
- **Consent and Statutory Authorizations**: Legal release of information under s. 18.4(1.1) and s. 76 of *The Child and Family Services Act*, along with date, digital signature capture, and witness identification.
- **Person Being Assessed (Identifying Information)**: Detailed demographic data (legal names, date of birth, gender, aliases/prior names, address, phone numbers, birthplace).
- **Identification Documents**: Selection and verification of two mandatory pieces of government identification, including conditional tracking for Driver's Licence numbers and alternative ID specifications.
- **Agency Request & Administrative Information**: Assessment purpose (Child Protection Concerns vs. Kinship/Customary Care Agreements), assigned case worker, prior assessment tracking, submitting designate credentials, contact channels, and formal request date.

The implementation is provided as a standard spreadsheet workbook (`.xlsx`), compiled XML (`.xml`), and a standalone interactive paper-style web preview (`preview.html`).

---

## Source Document

The design, question hierarchy, statutory citations, and validation rules in this project are derived directly from the authoritative government document:

- **Document Title**: Criminal Risk Assessment Request
- **Issuing Department**: Manitoba Families – Criminal Risk Assessment Unit (CRAU), Child Protection Branch
- **Office Location**: 201 - 114 Garry Street, Winnipeg, Manitoba R3C 4V5
- **Revision Date**: `2025-01-10`

---

## Project Structure

```text
.
├── Criminal_Risk_Assessment_Request.xlsx   # Core ODK XLSForm source workbook (survey, choices, settings)
├── Criminal_Risk_Assessment_Request.xml    # Compiled ODK XForms XML specification
├── preview.html                            # Standalone interactive two-page document preview
├── README.md                               # Comprehensive project documentation
├── data/
│   ├── Criminal Risk Assessment Request.pdf # Authoritative source PDF document
│   └── Sample XLS Form Reference.xlsx      # XLSForm convention reference workbook
└── docs/
    ├── form-analysis.md                    # Structural breakdown and requirement analysis
    ├── pdf-xlsform-mapping.md              # 1:1 mapping table of all PDF elements to XLSForm fields
    ├── preview.html                        # Document preview copy inside docs
    ├── pdf_page_1.png                      # Reference image of Page 1 from the source PDF
    ├── pdf_page_2.png                      # Reference image of Page 2 from the source PDF
    ├── extracted_img_p1_0.png              # Manitoba Families official header logo
    ├── extracted_img_p1_1.jpeg             # Driver's licence section 4d illustration
    └── extracted_img_p2_0.png              # Page 2 header logo
```

---

## Form Architecture & Logical Hierarchy

The form is organized into three primary group containers matching the source document:

```text
Criminal Risk Assessment Request
│
├── 1. Consent Section (group: consent_section)
│   ├── consent_notice (note: statutory legal statement)
│   ├── consent_date (date: optional)
│   ├── person_assessed_signature (image: appearance="signature")
│   └── unconsented_witness (text: witness name if consenting)
│
├── 2. Person Being Assessed (group: person_assessed)
│   ├── person_assessed_header_note (note: section header)
│   │
│   ├── 2.1 Identifying Information (group: identifying_information)
│   │   ├── identifying_info_note (note: "PLEASE PRINT CLEARLY")
│   │   ├── first_name (text: 1. FIRST NAME)
│   │   ├── second_name (text: 2. SECOND NAME)
│   │   ├── last_name (text: 3. LAST NAME)
│   │   ├── date_of_birth (date: 4. DATE OF BIRTH)
│   │   ├── gender (select_one gender: 5. MALE / FEMALE)
│   │   ├── other_last_names_used (text: 6. OTHER LAST NAMES USED)
│   │   ├── other_first_names_used (text: 7. OTHER FIRST NAMES USED/ALSO GOES BY)
│   │   ├── current_address (text: 8. CURRENT ADDRESS include postal code)
│   │   ├── current_ph_numbers (text: 9. CURRENT PH#s)
│   │   └── city_province_country_of_birth (text: 10. City/Province or Country of Birth)
│   │
│   └── 2.2 Identification Information (group: identification_information)
│       ├── identification_note (note: "*PLEASE NOTE: Subject's name must be identified...")
│       ├── identification_types (select_multiple identification_type: required="yes", constraint: count-selected(.) = 2)
│       ├── drivers_license_number (text: relevant when MB Driver's License selected)
│       └── other_id_specify (text: relevant when Other ID selected)
│
└── 3. Criminal Risk Assessment Request Information (group: request_information)
    ├── name_person_being_assessed (text: required="yes", constraint: must match Page 1 name)
    ├── agency_notice_note (note: CPIC / NICHE / Privacy Act statutory notice)
    ├── agency_submitting_request (text: required="yes", *NAME OF AGENCY SUBMITTING REQUEST)
    ├── risk_assessment_reason (select_one risk_assessment_reason: required="yes", 2 statutory options)
    ├── assigned_worker (text: required="yes", *ASSIGNED WORKER)
    ├── date_last_criminal_risk_assessment (date: optional, DATE OF LAST ASSESSMENT if known)
    ├── submitting_designate (text: required="yes", *SUBMITTING DESIGNATE)
    ├── designate_phone (text: required="yes", *DESIGNATE PH#)
    ├── designate_email (text: required="yes", *DESIGNATE EMAIL#)
    ├── designate_fax (text: optional, DESIGNATE FAX#)
    ├── request_date (date: required="yes", *REQUEST DATE)
    └── final_records_check_note (note: statutory disclaimer regarding criminal records check)
```

---

## Validation Logic & Business Rules

### 1. Mandatory Two Pieces of Identification
- **Question**: `identification_types` (`select_multiple identification_type`)
- **Required**: `yes` (`required="true()"`)
- **Constraint Expression**: `count-selected(.) = 2`
- **Constraint Message**: `Please select two pieces of identification.`
- **Behavior**:
  - 0 selections $\rightarrow$ Blocked by `required="true()"` rule.
  - 1 selection $\rightarrow$ Blocked by `count-selected(.) = 2`.
  - Exactly 2 selections $\rightarrow$ Passes validation.
  - 3+ selections $\rightarrow$ Blocked by `count-selected(.) = 2`.

### 2. Conditional Identification Details
- **Driver's Licence Number**: Field `drivers_license_number` has relevance `selected(${identification_types}, 'mb_drivers_license')`. It appears only when *MB Driver's License with Photo* is selected and disappears when unselected.
- **Other ID Specification**: Field `other_id_specify` has relevance `selected(${identification_types}, 'other_id')`. It appears only when *Other ID* is selected.

### 3. Page 2 Subject Name Cross-Section Verification
- **Field**: `name_person_being_assessed`
- **Requirement**: `required="yes"`
- **Hint**: `Must match information on page 1`
- **Constraint Expression**:
  ```text
  . = concat(${first_name}, ' ', ${second_name}, ' ', ${last_name}) or . = concat(${first_name}, ' ', ${last_name})
  ```
- **Constraint Message**: `Name must match information on page 1.`
- **Behavior**: Automatically validates the entered name against either the full three-part name (`First Middle Last`) or two-part name (`First Last`) entered on Page 1.

### 4. Required Fields Policy
In strict compliance with the source document instruction:
> **"NOTE – SECTIONS MARKED WITH AN ASTERISK (*) ARE REQUIRED"**

- **Required Fields (9 total)**:
  1. `identification_types` (Two pieces of ID mandatory per document terms)
  2. `name_person_being_assessed` (`*Must match information on page 1`)
  3. `agency_submitting_request` (`*NAME OF AGENCY SUBMITTING REQUEST:`)
  4. `risk_assessment_reason` (`*REASON FOR RISK ASSESSMENT:`)
  5. `assigned_worker` (`*ASSIGNED WORKER:`)
  6. `submitting_designate` (`*SUBMITTING DESIGNATE:`)
  7. `designate_phone` (`*DESIGNATE PH#:`)
  8. `designate_email` (`*DESIGNATE EMAIL#:`)
  9. `request_date` (`*REQUEST DATE:`)
- **Optional Fields (17 total)**:
  All Page 1 identifying fields (1–10) and consent elements, as well as Page 2 `date_last_criminal_risk_assessment` (marked `if known`) and `designate_fax` (no asterisk), are configured as optional.

### 5. Standardized Choice Lists
- **`gender`**: `male` (Male), `female` (Female)
- **`identification_type`**:
  - `birth_certificate` (Birth Certificate)
  - `social_insurance_card` (Social Insurance Card)
  - `manitoba_health_card` (Manitoba Health Card)
  - `treaty_card` (Treaty Card)
  - `other_id` (Other ID)
  - `mb_drivers_license` (MB Driver's License with Photo)
- **`risk_assessment_reason`**:
  - `child_protection_concerns` (Child Protection Concerns — With or Without Consent)
  - `place_of_safety_kinship_customary_care` (Place of Safety Kinship or Customary Care Agreement — Must have consent)

---

## How to Run & Validate

### Option 1: Mobile Devices via ODK Collect
1. Install **ODK Collect** on an Android device or emulator.
2. Transfer `Criminal_Risk_Assessment_Request.xml` to your device's `/forms/` directory, or upload `Criminal_Risk_Assessment_Request.xlsx` to your ODK Central server.
3. Open ODK Collect, select "Fill Blank Form", and choose "Criminal Risk Assessment Request".
4. Enter test data and verify signature capture, conditional fields, and validations.

### Option 2: Web Preview via Enketo (getodk.org)
1. Navigate to the online [ODK XLSForm Previewer](https://getodk.org/xlsform/).
2. Drag and drop `Criminal_Risk_Assessment_Request.xlsx` into the file upload box.
3. Click "Preview in Enketo".
4. Test selections, conditional reveals, and submit verification.

### Option 3: Local Standalone Interactive Preview (`preview.html`)
1. Open `preview.html` directly in any web browser (Chrome, Edge, Firefox, Safari).
2. The preview provides an authentic paper-document rendering matching the physical two-page Manitoba government form, complete with client-side execution of all validation logic:
   - Dynamic show/hide of Driver's Licence Number and Other ID inputs.
   - Enforcement of the exact-two identification constraint.
   - Live cross-section name match verification between Page 1 and Page 2.
   - Required field submission checking.
3. Use the browser's Print function (`Ctrl+P` / `Cmd+P`) to verify print stylesheet formatting for US Letter portrait output.

### Option 4: Command-Line Compilation (`pyxform`)
To recompile the workbook to XForms XML from the terminal:

```bash
# Install pyxform if needed
pip install pyxform

# Compile XLSForm to XML
python -m pyxform.xls2xform Criminal_Risk_Assessment_Request.xlsx Criminal_Risk_Assessment_Request.xml
```

---

## Technical Specifications

| Parameter | Value |
|-----------|-------|
| **Form ID (`form_id`)** | `criminal_risk_assessment_request` |
| **Form Title (`form_title`)** | Criminal Risk Assessment Request |
| **Version (`version`)** | `2025011001` |
| **Default Language** | English (`default_language = default`) |
| **ODK Signature Standard** | `type: image`, `appearance: signature` |
| **XForms Standard** | JavaRosa / OpenRosa XForms 1.0 compliant |
| **Compiler Compatibility** | PyXForm >= 4.5.0, ODK Validate (Java 8+) |

---

## Document Parity & Compliance Notes

1. **Exact Statutory Text Preserved**: All legal notices (s. 18.4(1.1) and s. 76 consent disclosure notice, CFS Agency CPIC/NICHE advisory notice, and the closing criminal records check disclaimer) match the source PDF verbatim without abbreviations.
2. **Page Separation**: The logical flow strictly separates Page 1 subject intake from Page 2 agency administration.
3. **No External Dependencies**: `preview.html` embeds all necessary image assets as inline data URIs, ensuring complete portability without broken external links.
