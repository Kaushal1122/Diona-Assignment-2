# Criminal Risk Assessment Request — Form Analysis

## 1. Source Information
- **PDF Filename**: `data/Criminal Risk Assessment Request.pdf`
- **PDF Revision Date**: `2025-01-10`
- **Number of Pages**: 2
- **Organization / Department**: 
  - Manitoba Families – Criminal Risk Assessment Unit (CRAU)
  - Child Protection Branch
  - 201 - 114 Garry Street, Winnipeg, Manitoba R3C 4V5
- **Form Title**: Criminal Risk Assessment Request
- **Statutory References**: *The Child and Family Services Act* (s. 18.4(1.1) and s. 76); *Privacy Act* (Federal Statute, Section 8).

---

## 2. Page 1 Structure

Page 1 serves primarily as the subject (person being assessed) consent, identity intake, and identification documentation page. The major sections on Page 1 are:

1. **Header & Department Identification**:
   - Title: `CRIMINAL RISK ASSESSMENT REQUEST`
   - Department branch and contact address: Manitoba Families - Criminal Risk Assessment Unit, Child Protection Branch, 201 - 114 Garry Street, Winnipeg, MB R3C 4V5.
2. **Consent for Criminal Risk Assessment and Release of Information**:
   - Legal authorization text authorizing the Criminal Risk Assessment Unit (CRAU) to conduct inquiries with Winnipeg Police Service (WPS), RCMP, and other law enforcement agencies under s. 18.4(1.1) and s. 76 of *The Child and Family Services Act*.
   - `Date:` (Date field).
   - `Signature of person being assessed:` (Signature field).
   - `Unconsented` (Checkbox field).
   - `Witness (if consenting):` (Text field).
3. **Person Being Assessed — Identifying Information (`PLEASE PRINT CLEARLY`)**:
   - `1. FIRST NAME:`
   - `2. SECOND NAME:`
   - `3. LAST NAME:`
   - `4. DATE OF BIRTH:` (Divided visually into Day, Month, Year).
   - `5.` Gender selection (`MALE`, `FEMALE`).
   - `6. OTHER LAST NAMES USED:`
   - `7. OTHER FIRST NAMES USED/ALSO GOES BY:`
   - `8. CURRENT ADDRESS (include postal code):`
   - `9. CURRENT PH#s:`
   - `10. City/Province or Country of Birth:`
4. **Identification Information**:
   - Note header: `*PLEASE NOTE: Subject's name must be identified with TWO PIECES OF IDENTIFICATION (MB D/L & photo ID is preferable):`
   - Predefined ID checkboxes:
     - `Birth Certificate`
     - `Social Insurance Card`
     - `Manitoba Health Card`
     - `Treaty Card`
     - `Other (specify ID):` (Checkbox + Text input)
     - `MB Driver's License with Photo - licence number (section 4d on licence):` (Checkbox + Text input for licence number)
5. **Page 1 Footer**:
   - Document identifier: `Criminal Risk Assessment Request Revision date: 2025-01-10 1`

---

## 3. Page 2 Structure

Page 2 serves as the Child and Family Services (CFS) agency submission section, containing legal notices, verification of the subject's identity, and the formal assessment request details. The major sections on Page 2 are:

1. **Page Header**:
   - Title: `CRIMINAL RISK ASSESSMENT REQUEST`
2. **Person Being Assessed Confirmation**:
   - `NAME OF PERSON BEING ASSESSED:`
   - Sub-instruction: `*Must match information on page 1`
3. **CFS Agency Designate Legal Notice / Instructions**:
   - Title: `IT IS IMPORTANT THAT THE CFS AGENCY DESIGNATE READS AND UNDERSTANDS THE FOLLOWING:`
   - Full advisory text regarding CPIC / WPS NICHE checks, limitations regarding vulnerable sector searches and pardons, privacy under Section 8 of the Privacy Act, fingerprint verification for identity disputes, and fees for service.
4. **General Form Instruction**:
   - `NOTE – SECTIONS MARKED WITH AN ASTERISK (*) ARE REQUIRED`
5. **Criminal Risk Assessment Request Information**:
   - `*NAME OF AGENCY SUBMITTING REQUEST:`
   - `*REASON FOR RISK ASSESSMENT:`
     - Sub-grouping: "With or Without Consent:" -> `Child Protection Concerns`
     - Sub-grouping: "Must have consent:" -> `Place of Safety`, `Kinship or Customary Care Agreement`
   - `*ASSIGNED WORKER:`
   - `DATE OF LAST CRIMINAL RISK ASSESSMENT (if known):`
   - `*SUBMITTING DESIGNATE:`
   - `*DESIGNATE PH#:`
   - `*DESIGNATE EMAIL#:`
   - `DESIGNATE FAX#`
   - `*REQUEST DATE:`
6. **Closing Advisory Note**:
   - `NOTE: The assessment completed by the Criminal Risk Assessment Unit of the Department of Families Child Protection Branch does not replace a criminal records check.`
7. **Page 2 Footer**:
   - Document identifier: `Criminal Risk Assessment Request Revision date: 2025-01-10 2`

---

## 4. Required Fields

The PDF explicitly establishes the requirement policy on Page 2:
> **"NOTE – SECTIONS MARKED WITH AN ASTERISK (*) ARE REQUIRED"**

Per instructions, only fields explicitly marked as required by the PDF are classified as required.

| PDF Field | Page | Required? | Evidence / Reason |
|-----------|------|-----------|-------------------|
| Date (Consent) | Page 1 | No | Not marked with an asterisk (*). |
| Signature of person being assessed | Page 1 | No | Not marked with an asterisk (*). Can be skipped if "Unconsented" is checked. |
| Unconsented | Page 1 | No | Optional checkbox indicator; not marked with an asterisk (*). |
| Witness (if consenting) | Page 1 | No | Marked "(if consenting)"; not marked with an asterisk (*). |
| 1. FIRST NAME | Page 1 | No | Not marked with an asterisk (*). |
| 2. SECOND NAME | Page 1 | No | Not marked with an asterisk (*). Optional middle/second name. |
| 3. LAST NAME | Page 1 | No | Not marked with an asterisk (*). |
| 4. DATE OF BIRTH | Page 1 | No | Not marked with an asterisk (*). |
| 5. Gender (MALE / FEMALE) | Page 1 | No | Not marked with an asterisk (*). |
| 6. OTHER LAST NAMES USED | Page 1 | No | Not marked with an asterisk (*). Optional alias/maiden name. |
| 7. OTHER FIRST NAMES USED/ALSO GOES BY | Page 1 | No | Not marked with an asterisk (*). Optional alias. |
| 8. CURRENT ADDRESS (include postal code) | Page 1 | No | Not marked with an asterisk (*). |
| 9. CURRENT PH#s | Page 1 | No | Not marked with an asterisk (*). |
| 10. City/Province or Country of Birth | Page 1 | No | Not marked with an asterisk (*). |
| Identification Pieces Selection | Page 1 | Ambiguous | Instruction text has an asterisk (`*PLEASE NOTE: Subject's name must be identified with TWO PIECES OF IDENTIFICATION...`), but individual checkboxes do not have asterisks. The asterisk acts as a callout note. |
| Other (specify ID) text | Page 1 | No | Not marked with an asterisk (*). |
| MB Driver's License number (section 4d) | Page 1 | No | Not marked with an asterisk (*). |
| NAME OF PERSON BEING ASSESSED | Page 2 | Yes (via constraint/instruction) | Sub-label explicitly states `*Must match information on page 1` with an asterisk (*). |
| *NAME OF AGENCY SUBMITTING REQUEST | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |
| *REASON FOR RISK ASSESSMENT | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |
| *ASSIGNED WORKER | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |
| DATE OF LAST CRIMINAL RISK ASSESSMENT (if known) | Page 2 | No | Not marked with an asterisk (*); explicitly qualified with "(if known)". |
| *SUBMITTING DESIGNATE | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |
| *DESIGNATE PH# | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |
| *DESIGNATE EMAIL# | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |
| DESIGNATE FAX# | Page 2 | No | Not marked with an asterisk (*). Optional contact method. |
| *REQUEST DATE | Page 2 | Yes | Explicitly prefixed with an asterisk (*). |

---

## 5. Choice Fields

| Field | Choices Shown in PDF | Selection Type | Ambiguity / Notes |
|-------|----------------------|----------------|-------------------|
| **Gender** (Page 1, item 5) | `MALE`, `FEMALE` | Single-select (`select_one`) | PDF uses mutually exclusive radio buttons (export values `Male`, `Female`). Standard ODK practice may consider whether non-binary options should be discussed, but PDF strictly displays only `MALE` and `FEMALE`. |
| **Pieces of Identification** (Page 1, ID section) | - `Birth Certificate`<br>- `Social Insurance Card`<br>- `Manitoba Health Card`<br>- `Treaty Card`<br>- `Other (specify ID)`<br>- `MB Driver's License with Photo` | Multi-select (`select_multiple`) or individual checkboxes | PDF presents them as separate checkboxes where two pieces must be chosen. In XLSForm, this can be modeled either as a `select_multiple` list or individual boolean questions. A `select_multiple` is standard ODK practice. |
| **Reason for Risk Assessment** (Page 2) | - `Child Protection Concerns` (With or Without Consent)<br>- `Place of Safety` (Must have consent)<br>- `Kinship or Customary Care Agreement` (Must have consent) | Single-select (`select_one`) | PDF uses radio button group (export values `CPC`, `POS`, `AGRMT`). It is strictly a single-choice field divided conceptually into two legal tiers. |

---

## 6. Conditional Logic Candidates

These fields will require conditional relevance (`relevant` expression in XLSForm) during subsequent stages:

1. **Consent vs. Unconsented Flow**:
   - If `Unconsented` is selected on Page 1:
     - The subject signature is not applicable / skipped.
     - The `Witness (if consenting)` field is not applicable / hidden (PDF label explicitly says: `Witness (if consenting)`).
     - Under `*REASON FOR RISK ASSESSMENT` on Page 2, the options `Place of Safety` and `Kinship or Customary Care Agreement` ("Must have consent") must either be constrained or filtered out, because only `Child Protection Concerns` can proceed "With or Without Consent".
2. **Identification "Other" Specification**:
   - The text field for `Other (specify ID)` should only appear when the `Other` checkbox / choice is selected.
3. **MB Driver's License Details**:
   - The input field `MB Driver's License with Photo - licence number (section 4d on licence)` should only appear or be relevant if the `MB Driver's License with Photo` ID option is selected.
4. **Previous Assessment Date**:
   - Field `DATE OF LAST CRIMINAL RISK ASSESSMENT (if known)` may be conditioned on a preceding question (e.g. "Has a previous criminal risk assessment been conducted?") or left as an optional date input.

---

## 7. Validation Candidates

Fields that may require constraints (`constraint` and `constraint_message`) in later stages:

1. **Date of Birth**:
   - Must be a valid date in the past (`. <= today()`).
2. **Two Pieces of Identification Constraint**:
   - The PDF instructs: `"Subject's name must be identified with TWO PIECES OF IDENTIFICATION"`.
   - If implemented as `select_multiple`, a constraint `count-selected(.) >= 2` with an informative message.
3. **Driver's License Number**:
   - Manitoba driver's license numbers typically follow a specific format (e.g. alphanumeric length/pattern).
4. **Designate Email**:
   - Standard email regex validation (`regex(., '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$')`).
5. **Designate Phone Number & Fax**:
   - Standard 10-digit North American phone number validation / formatting.
6. **Request Date**:
   - Must be a valid date, typically not in the distant future (`. <= today()`).
7. **Subject Name Matching**:
   - On Page 2, `NAME OF PERSON BEING ASSESSED` states `*Must match information on page 1`. In ODK, this can be automatically populated via a `calculate` field or validated to match the concatenated First Name and Last Name from Page 1.

---

## 8. Special XLSForm Treatment

1. **Legal & Explanatory Text**:
   - Consent statement on Page 1 and Agency warning on Page 2 are long statutory paragraphs. In XLSForm, these should be rendered using `note` question types with clear markdown formatting.
2. **Signatures**:
   - `Signature of person being assessed` should use ODK `signature` (or `image` with `appearance="signature"`), capturing digital on-screen signing.
3. **Group Structuring**:
   - High-level sections must use `begin_group` and `end_group` to cleanly delineate sections. Groups can utilize `field-list` appearance for single-screen page layout mirroring the physical PDF pages.
4. **Calculations**:
   - Concatenating First Name, Second Name, and Last Name to display or cross-check on Page 2.

---

## 9. Ambiguities / Decisions Required

1. **Page 1 Question Requirement Ambiguity**:
   - The PDF explicitly states: `"NOTE – SECTIONS MARKED WITH AN ASTERISK (*) ARE REQUIRED"` on Page 2. Questions 1 through 10 on Page 1 do not have asterisks in the printed form. However, a criminal risk assessment search through CPIC/NICHE requires at minimum First Name, Last Name, and Date of Birth to execute.
    - *Design Decision*: Keep strictly literal to the PDF (required where asterisk exists and for two pieces of ID) ensuring accurate statutory alignment.
2. **Identification Mechanism**:
   - Should ID pieces be represented as a single `select_multiple identification_types` question, or as individual boolean questions? (A `select_multiple` is cleaner and standard in ODK).
3. **Date of Birth Input Representation**:
   - In the PDF, DOB has three separate boxes: `Day`, `Month`, `Year`. In ODK, standard practice is a single `date` question with native calendar/date picker, or three integer fields. A native `date` widget is cleaner and avoids invalid dates like February 31.
4. **Name Confirmation on Page 2**:
   - In a paper form, Page 2 repeats the subject's name in case pages are detached. In a digital XLSForm, this can be an automatic read-only note or calculate field, or an explicit re-entry verification.
