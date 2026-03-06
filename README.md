# Katelia-FinQA
Here is the complete, official `README.md` file ready to be pasted directly into your GitHub repository. It serves as the front page of your project, commanding respect, explaining the novel architecture, and strictly enforcing your CC BY-NC-SA 4.0 license.

---

```markdown
# Katelia FinQA ⚙️📊
**A Mechanical Engineering Approach to AI Financial Governance**

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Architect](https://img.shields.io/badge/Architect-Muzzammil%20Katelia-blue)](#)
[![Deployment](https://img.shields.io/badge/Entity-Minimax%20Sustainable%20AI%20LTD.-green)](#)

> **Katelia FinQA** is a novel AI accounting architecture designed for the MSAI CRM. It translates physical mechanical engineering tolerances into strict digital data governance. OCR-extracted financial data must pass rigid ISO 9001 QA gates or hit a Non-Conformance (NCR) queue, ensuring zero ledger corruption.

## 💡 The Architecture: Katelia Data Tolerance Framework
Developed by Muzzammil Katelia, this framework bridges industrial engineering and FinTech. Instead of relying on standard software exception handling, Katelia FinQA treats financial inputs like physical manufactured parts, applying **Clifford Matthews' "Limits and Fits" principles** to digital accounting.

### Core Mechanisms
* **The OCR Vision Engine:** Extracts receipt text, amounts, and dates with an AI confidence score.
* **Mechanical-to-Digital Tolerances:** Mathematical variance (e.g., Subtotal + Tax ≠ Total) is treated as a physical defect. If the variance exceeds the hard-coded limit, the data halts.
* **The NCR Holding Pen:** Defective data (bad math, low OCR confidence, unauthorized business users) is routed to a strict Non-Conformance Report (NCR) queue. It never touches the MSAI CRM budget.
* **Traceability Hash:** Every verified ledger entry is stamped with an ISO 9001-compliant tracking ID linking back to the original scan.

## 🚀 Getting Started

### Prerequisites
* Python 3.8+
* An active MSAI CRM instance (or simulated endpoint)

### Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/katelia-finqa.git](https://github.com/yourusername/katelia-finqa.git)

```

2. Navigate to the directory:
```bash
cd katelia-finqa

```


3. Run the backend engine tests:
```bash
python msai_qa_engine.py

```



## ⚖️ License & Copyright

**© 2026 Muzzammil Katelia.** Deployed under **Minimax Sustainable AI LTD.**

This project is licensed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)**.

You are free to Share and Adapt this material under the following terms:

* **Attribution (BY):** You must give appropriate credit to Muzzammil Katelia.
* **NonCommercial (NC):** You may NOT use the material for commercial purposes without explicit permission.
* **ShareAlike (SA):** If you remix, transform, or build upon the material, you must distribute your contributions under the same license.

Full license terms: [https://creativecommons.org/licenses/by-nc-sa/4.0/](https://creativecommons.org/licenses/by-nc-sa/4.0/)

```

***

That markdown file will look incredibly sharp and professional on GitHub, instantly establishing both your innovation and your legal boundaries. 

# ==============================================================================
# © 2026 Muzzammil Katelia. Licensed under CC BY 4.0.
# Project: MSAI CRM Accounting AI (Katelia Data Tolerance Architecture)
# Corporate Deployment: Minimax Sustainable AI LTD.
# ==============================================================================

import time
import uuid

class QualityAssuranceSpecs:
    """Clifford Matthews-style tolerances applied to financial data."""
    MAX_VARIANCE = 0.02          # Allowable rounding error tolerance (£)
    MIN_OCR_CONFIDENCE = 0.88    # AI must be 88% sure of the extracted text
    AUTHORIZED_VENDORS = ["user_muzzammil_01", "user_roger_02"] # Approved Business Users

def simulate_ocr_extraction(image_file, vendor_id, mock_variance=0.0):
    """Step 1: AI Vision/OCR Extraction (Simulated for testing)"""
    print(f"Scanning document: {image_file}...")
    time.sleep(1) # Simulating AI processing time
    
    return {
        "Vendor_ID": vendor_id,           # The Business User submitting
        "Merchant": "B&Q Hull",           # The physical store
        "Date": "2026-03-06",
        "Subtotal": 100.00,
        "Tax": 20.00,
        "Total_Amount": 120.00 + mock_variance, # Adding variance to test tolerances
        "Confidence_Score": 0.92          
    }

def qa_inspection_gate(data):
    """Step 2: The NCR (Non-Conformance) Inspection"""
    print("Executing ISO 9001 / Matthews QA Gate...")
    
    # QA Check 1: Vendor Authorization (Is the Business User valid?)
    if data["Vendor_ID"] not in QualityAssuranceSpecs.AUTHORIZED_VENDORS:
        return "NCR FLAG: Unauthorized Vendor (Business User)."

    # QA Check 2: Mathematical Tolerance (Do the parts fit?)
    calculated_total = data["Subtotal"] + data["Tax"]
    variance = abs(calculated_total - data["Total_Amount"])
    if variance > QualityAssuranceSpecs.MAX_VARIANCE:
        return f"NCR FLAG: Math fails tolerance check. Variance: £{variance:.2f}"

    # QA Check 3: Material Readability (Is the scan quality high enough?)
    if data["Confidence_Score"] < QualityAssuranceSpecs.MIN_OCR_CONFIDENCE:
        return f"NCR FLAG: Low OCR confidence ({data['Confidence_Score']}). Manual review required."

    return "PASS"

def push_to_msai_crm(clean_data):
    """Step 3: API Payload to the CRM Ledger"""
    traceability_hash = f"SCAN-{uuid.uuid4().hex[:8].upper()}"
    
    crm_payload = {
        "transaction_id": traceability_hash,
        "business_user": clean_data["Vendor_ID"],
        "merchant_name": clean_data["Merchant"],
        "transaction_date": clean_data["Date"],
        "ledger_amount": clean_data["Total_Amount"],
        "qa_timestamp": time.time(),
        "status": "Verified - ISO9001 Compliant"
    }
    
    print(f"✅ SUCCESS: Data passed QA. Traceability Hash generated: {traceability_hash}")
    print(f"📡 Pushing payload to MSAI CRM: {crm_payload}\n")
    # In production: requests.post("https://api.msaicrm.com/v1/ledger", json=crm_payload)

def process_expense(image_file, vendor_id, mock_variance=0.0):
    """Main System Engine Pipeline"""
    print(f"\n--- INITIATING PROCESS FOR: {image_file} | VENDOR: {vendor_id} ---")
    
    # 1. Extract
    raw_data = simulate_ocr_extraction(image_file, vendor_id, mock_variance)
    
    # 2. Inspect
    inspection_result = qa_inspection_gate(raw_data)
    
    # 3. Route
    if inspection_result == "PASS":
        push_to_msai_crm(raw_data)
    else:
        print(f"❌ REJECTED: Routing to NCR Holding Queue.")
        print(f"⚠️ Reason: {inspection_result}\n")

# ==========================================
# 🛠️ SYSTEM TESTS (Run this file to test)
# ==========================================
if __name__ == "__main__":
    # Test 1: Perfect Scan (Should Pass)
    process_expense("perfect_receipt.jpg", "user_muzzammil_01", mock_variance=0.0)
    
    # Test 2: Bad Math / Scanner Error (Should Fail to NCR)
    process_expense("crumpled_receipt.jpg", "user_muzzammil_01", mock_variance=1.50)
    
    # Test 3: Unauthorized Business User (Should Fail to NCR)
    process_expense("rogue_invoice.pdf", "unauthorized_user_99", mock_variance=0.0)
```
