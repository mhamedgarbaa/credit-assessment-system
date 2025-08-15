# Credit Assessment System

## Overview

The Credit Assessment System is an AI-powered application that provides automated credit risk evaluations with detailed explanations and factor analysis. This system combines state-of-the-art language models, document processing capabilities, and interactive visualizations to make credit scoring more transparent and accessible.

![Credit Assessment System](https://img.shields.io/badge/AI-Credit%20Scoring-blue)
![Python](https://img.shields.io/badge/Python-3.8+-green)
![Transformers](https://img.shields.io/badge/Transformers-4.0+-orange)
![Gradio](https://img.shields.io/badge/Gradio-UI-brightgreen)

## Features

- **Multi-source Input**: Process applicant information from text input, file uploads (PDF, Word, Text), or URLs
- **AI-powered Credit Scoring**: Utilizes specialized financial language models to generate credit scores (300-850 scale)
- **Explainable AI**: TokenSHAP analysis to identify which factors most influenced the credit decision
- **Document Processing**: Automatic extraction of relevant information from various document formats
- **Policy Alignment**: Credit decisions aligned with established credit policies and standards
- **Dual-model Architecture**: 
  - Primary model (FinMA) for initial credit assessment
  - Judge model (Mistral) for final recommendations and explanations
- **Interactive UI**: Clean, responsive interface with real-time visualizations

## System Architecture

```
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│                 │         │                 │         │                 │
│  User Interface │ ───────▶│ Text Processing │ ───────▶│  Credit Scoring │
│    (Gradio)     │         │    Pipeline     │         │     Models      │
│                 │         │                 │         │                 │
└─────────────────┘         └─────────────────┘         └─────────────────┘
                                                                 │
┌─────────────────┐         ┌─────────────────┐                 ▼
│                 │         │                 │         ┌─────────────────┐
│   Visualization │ ◀─────── │ Explainability  │ ◀──────│  AlignRAG       │
│    Dashboard    │         │    Analysis     │         │  Knowledge Base │
│                 │         │                 │         │                 │
└─────────────────┘         └─────────────────┘         └─────────────────┘
```

## Technical Components

### Models
- **FinMA Model**: Specialized financial model for credit assessment
- **Mistral 7B Instruct**: LLM for final judgment and natural language explanations
- **TokenSHAP**: Explainability framework for understanding model decisions

### Libraries & Dependencies
- **huggingface_hub**: For model access and management
- **transformers, torch, bitsandbytes**: For model loading and inference
- **pandas, numpy**: For data processing and numerical operations
- **gradio**: For building the web interface
- **PyMuPDF (fitz), python-docx, PyPDF2**: For document processing
- **plotly**: For interactive visualizations
- **beautifulsoup4, newspaper3k**: For web content extraction
- **sklearn**: For TF-IDF vectorization in the knowledge base

## Implementation Details

### AlignRAG System
The application implements a Retrieval-Augmented Generation system (AlignRAG) that ensures credit decisions are consistent with established credit policies and standards. It maintains a knowledge base of:
- Credit policies
- Industry standards
- Previous credit decisions (precedents)
- Regulatory requirements

### Credit Scoring Process

1. **Input Processing**:
   - Text extraction from documents (PDF, Word) or URLs
   - Text cleaning and normalization

2. **Factor Extraction**:
   - Identification of key credit factors (income, debt, employment history, etc.)
   - Assessment of factor completeness

3. **Model Scoring**:
   - Primary credit score generation (300-850 scale)
   - Pattern matching for score extraction from model output

4. **Policy Alignment**:
   - Retrieval of relevant policies and standards
   - Calculation of alignment score with established policies

5. **Explainability Analysis**:
   - TokenSHAP analysis to determine factor importance
   - Visualization of factor impact

6. **Final Judgment**:
   - Secondary model review and recommendation
   - Final decision (approve/reject) with explanation

## User Interface

The application provides a clean, intuitive interface built with Gradio:

- **Input Tab**: Multiple methods to provide applicant information
  - Direct text input
  - File upload (PDF, Word, Text)
  - URL input

- **Results Display**:
  - Credit score with risk level visualization
  - Factor impact analysis chart
  - Detailed explanation of the decision
  - Judge's recommendation
  - Raw application text view
  - Full assessment report

- **Advanced Settings**:
  - Explanation detail level
  - Factor analysis method selection
  - Sampling parameters for TokenSHAP analysis

## Getting Started

### Prerequisites
- Python 3.8+
- CUDA-compatible GPU (recommended)
- Access to Hugging Face models

### Installation

1. Clone the repository:
```bash
git clone https://github.com/mhamedgarbaa/credit-assessment-system.git
cd credit-assessment-system
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Set up Hugging Face access:
```python
from huggingface_hub import login
login(token="your_hf_token")
```

4. Launch the application:
```bash
python app.py
```

## Usage Examples

### Example 1: Basic Credit Assessment

1. Enter applicant information in the text box:
```
Applicant Information:
Name: John Smith
Age: 35
Income: $75,000 annually
Current Debt: $12,000 in credit card debt, $150,000 mortgage
Payment History: One late payment in the last 24 months
Credit History: 10 years
Savings: $25,000
Job Stability: 5 years at current position
```

2. Click "Analyze Credit Application"
3. Review the credit score, factor analysis, and recommendation

### Example 2: Document Upload

1. Upload a PDF or Word document containing applicant information
2. Adjust factor analysis settings if needed
3. Click "Analyze Credit Application"
4. Review results and export if needed

## Future Enhancements

- Integration with external credit databases
- Support for additional document formats
- Enhanced multi-language support
- Customizable credit policy integration
- Batch processing for multiple applications
- API endpoints for system integration

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Hugging Face for providing access to transformer models
- The open-source community for the various libraries used in this project
- Financial domain experts for guidance on credit policy implementation

---

*Note: This credit assessment system is intended for demonstration and educational purposes. It should not be used as the sole basis for making actual credit decisions without appropriate validation and compliance review.*
