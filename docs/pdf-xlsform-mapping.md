# PDF to XLSForm Mapping

This document provides the complete 1:1 mapping between items in the source document `data/Criminal Risk Assessment Request.pdf` and the corresponding questions and logic in `Criminal_Risk_Assessment_Request.xlsx`.

---

## 1. Page 1 — Consent Section (`consent_section`)

| PDF Item | XLSForm Name | Type | Required | Details / Appearance |
|----------|--------------|------|:--------:|:---------------------|
| Consent text | `consent_notice` | `note` | No | Statutory text citing s. 18.4(1.1) and s. 76 of *The Child and Family Services Act* |
| Date | `consent_date` | `date` | No | Standard date picker |
| Signature of person being assessed | `person_assessed_signature` | `image` | No | `appearance: signature` (interactive signature capture canvas) |
| Unconsented Witness (if consenting) | `unconsented_witness` | `text` | No | Free-text entry field |

---

## 2. Page 1 — Identifying Information (`identifying_information`)

| PDF Item | PDF Label | XLSForm Name | Type | Required | Notes / Choices |
|:--------:|-----------|--------------|------|:--------:|:----------------|
| — | PLEASE PRINT CLEARLY | `identifying_info_note` | `note` | No | Centered document divider note |
| 1 | First Name | `first_name` | `text` | No | Subject's first legal name |
| 2 | Second Name | `second_name` | `text` | No | Subject's middle / second legal name |
| 3 | Last Name | `last_name` | `text` | No | Subject's legal last name |
| 4 | Date of Birth | `date_of_birth` | `date` | No | Subject's date of birth |
| 5 | Gender | `gender` | `select_one gender` | No | Choices: `male`, `female` |
| 6 | Other Last Names Used | `other_last_names_used` | `text` | No | Maiden name, alias, etc. |
| 7 | Other First Names Used/Also Goes By | `other_first_names_used` | `text` | No | Nickname, alias, etc. |
| 8 | Current Address (include postal code) | `current_address` | `text` | No | Full street, city, postal code |
| 9 | Current PH#s | `current_ph_numbers` | `text` | No | Subject's telephone numbers |
| 10 | City/Province or Country of Birth | `city_province_country_of_birth` | `text` | No | Birthplace geographic location |

---

## 3. Page 1 — Identification Information (`identification_information`)

| PDF Field | XLSForm Name | Type | Choices | Constraints / Relevance | Required |
|-----------|--------------|------|---------|-------------------------|:--------:|
| *PLEASE NOTE... (ID note) | `identification_note` | `note` | — | Text noting requirement for 2 pieces of ID | No |
| Two Pieces of Identification | `identification_types` | `select_multiple identification_type` | 6 identification choices | `count-selected(.) = 2`<br>Message: *"Please select two pieces of identification."* | **Yes** |
| Driver's Licence Number | `drivers_license_number` | `text` | — | `relevant: selected(${identification_types}, 'mb_drivers_license')` | No |
| Other (specify ID) | `other_id_specify` | `text` | — | `relevant: selected(${identification_types}, 'other_id')` | No |

---

## 4. Page 2 — Criminal Risk Assessment Request Information (`request_information`)

| PDF Field | XLSForm Name | Type | Choices | Constraints / Details | Required |
|-----------|--------------|------|---------|----------------------|:--------:|
| NAME OF PERSON BEING ASSESSED: (*Must match information on page 1) | `name_person_being_assessed` | `text` | — | `. = concat(${first_name}, ' ', ${second_name}, ' ', ${last_name}) or . = concat(${first_name}, ' ', ${last_name})`<br>Message: *"Name must match information on page 1."* | **Yes** |
| CFS Agency Designate Advisory Notice | `agency_notice_note` | `note` | — | Full verbatim statutory advisory text (CPIC / NICHE / Privacy Act) | No |
| *NAME OF AGENCY SUBMITTING REQUEST: | `agency_submitting_request` | `text` | — | Submitting Child and Family Services Agency | **Yes** |
| *REASON FOR RISK ASSESSMENT: | `risk_assessment_reason` | `select_one risk_assessment_reason` | 2 source choices | Radio selection of statutory reasons | **Yes** |
| *ASSIGNED WORKER: | `assigned_worker` | `text` | — | Case worker name | **Yes** |
| DATE OF LAST CRIMINAL RISK ASSESSMENT (if known): | `date_last_criminal_risk_assessment` | `date` | — | Optional date picker (no asterisk) | **No** |
| *SUBMITTING DESIGNATE: | `submitting_designate` | `text` | — | Agency designate authorizing the request | **Yes** |
| *DESIGNATE PH#: | `designate_phone` | `text` | — | Telephone number for designate | **Yes** |
| *DESIGNATE EMAIL#: | `designate_email` | `text` | — | Official email address for designate | **Yes** |
| DESIGNATE FAX# | `designate_fax` | `text` | — | Optional facsimile number (no asterisk) | **No** |
| *REQUEST DATE: | `request_date` | `date` | — | Date of request submission | **Yes** |
| Final Statutory Notice ("does not replace a criminal records check") | `final_records_check_note` | `note` | — | Non-input disclaimer note | No |

---

## 5. Choice Lists Defined

### `gender`
| List Name | Name (Value) | Label |
|-----------|--------------|-------|
| `gender`  | `male`       | Male  |
| `gender`  | `female`     | Female |

### `identification_type`
| List Name | Name (Value) | Label |
|-----------|--------------|-------|
| `identification_type` | `birth_certificate` | Birth Certificate |
| `identification_type` | `social_insurance_card` | Social Insurance Card |
| `identification_type` | `manitoba_health_card` | Manitoba Health Card |
| `identification_type` | `treaty_card` | Treaty Card |
| `identification_type` | `other_id` | Other ID |
| `identification_type` | `mb_drivers_license` | MB Driver's License with Photo |

### `risk_assessment_reason`
| List Name | Name (Value) | Label |
|-----------|--------------|-------|
| `risk_assessment_reason` | `child_protection_concerns` | Child Protection Concerns |
| `risk_assessment_reason` | `place_of_safety_kinship_customary_care` | Place of Safety Kinship or Customary Care Agreement |
