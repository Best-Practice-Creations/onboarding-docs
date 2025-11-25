# Volentis AI - Onboarding Documentation

Welcome to the Volentis AI onboarding documentation repository. This is your central resource for integrating and deploying the Volentis HR Agent within your organization.

## 🤖 About Volentis AI

**Volentis AI** is a secure, EU-hosted AI assistant designed specifically for HR teams. The Volentis HR Agent is an always-on assistant that empowers your HR department and employees with instant, accurate information.

### What the HR Agent Does

💬 **Answers HR Questions**
- Instantly responds to queries from your CAO, employee handbook, or HR policies
- Provides accurate information with source citations
- Available 24/7 in your organization's language

🔄 **Guides Through Workflows**
- Step-by-step guidance for leave requests
- Expense claim submissions
- Onboarding procedures
- Training enrollments
- Manager and staff workflows

📋 **Summarizes Policies & Legislation**
- Clear explanations of complex policies
- Legislation summaries with citations
- Source references for every answer

🔗 **Integrates with Your Systems**
- AFAS
- SAP
- Microsoft Dynamics
- Workday
- Personio
- Outlook calendars
- SharePoint & Microsoft 365

### Technology & Trust

Volentis AI is built on a foundation of security and transparency:

- 🔐 **Multi-source RAG architecture** - Retrieves answers directly from your documents and systems
- 🏢 **Dedicated isolated environment** - Each organization gets its own secure instance
- 📖 **Full transparency** - Every answer includes source document and citation
- ✅ **100% GDPR-compliant** - EU-native infrastructure and data handling
- 🇪🇺 **EU-hosted** - Your data stays within European Union borders

### Measurable Results

Organizations using Volentis AI typically see:

- 📉 **50-70% reduction** in HR service tickets
- 🕐 **24/7 self-service** for all employees
- 😊 **+30% increase** in employee satisfaction
- ⚡ **Instant responses** instead of hours or days
- 🚀 **Weeks not months** to deploy

## 📚 What This Repository Is For

This repository contains **technical onboarding documentation** to help IT administrators and system integrators:

✅ Set up Microsoft Entra ID (Azure AD) app registrations  
✅ Configure API permissions for SharePoint and Microsoft Graph  
✅ Manage authentication credentials securely  
✅ Integrate Volentis AI with your Microsoft 365 environment  
✅ Troubleshoot common integration issues  

## 🎯 Who Should Use This Documentation

This documentation is designed for:

- **IT Administrators** - Setting up authentication and permissions
- **System Integrators** - Connecting Volentis AI to Microsoft 365
- **Security Teams** - Reviewing compliance and security configurations
- **Project Managers** - Planning and tracking deployment phases

> 💡 **Note**: This is not end-user documentation. For information about using the Volentis HR Agent as an employee or HR professional, please refer to your organization's internal training materials or contact Volentis AI support.

## 📖 Available Guides

### 🔐 [Microsoft Entra App Registration Guide](entra-app-registration.md)

**Complete technical guide for setting up authentication with Microsoft 365**

This comprehensive guide covers:
- Creating an app registration in Microsoft Entra ID (Azure AD)
- Configuring required API permissions for Microsoft Graph and SharePoint
- Granting administrator consent
- Creating and managing client secrets securely
- Collecting configuration values (Tenant ID, Client ID, Client Secret)
- Connecting Volentis AI to your Microsoft 365 tenant
- Step-by-step instructions
- Troubleshooting common issues

**Time to complete**: 15-20 minutes  
**Required role**: Application Administrator or Global Administrator

👉 **[Get Started with Entra Setup →](entra-app-registration.md)**

---

## 🚀 Quick Start

To integrate Volentis AI with your organization:

1. **Review Prerequisites**
   - Ensure you have admin access to Microsoft Entra ID
   - Verify you have appropriate permissions (Application Administrator or Global Administrator)
   - Have your Volentis AI account ready

2. **Follow the Entra App Registration Guide**
   - Complete all steps in the [Entra App Registration Guide](entra-app-registration.md)
   - Collect your Tenant ID, Client ID, and Client Secret
   - Keep credentials secure

3. **Configure Volentis AI**
   - Enter your credentials in the Volentis AI application
   - Test the connection
   - Upload your HR documents to SharePoint

4. **Deploy to Your Team**
   - Run pilot tests with HR team
   - Gather feedback
   - Roll out organization-wide

## 🔒 Security & Compliance

Volentis AI meets the highest standards for enterprise security:

### GDPR Compliance
- **100% GDPR-compliant** - Full adherence to EU data protection regulations
- **EU data residency** - All data processed and stored within the EU
- **Right to erasure** - Full control over your data
- **Data processing agreements** - Clear legal framework

### Enterprise Security
- **Dedicated environments** - Isolated infrastructure per organization
- **No data sharing** - Your data is never used to train models
- **OAuth 2.0 authentication** - Industry-standard security
- **Encrypted at rest and in transit** - Military-grade encryption
- **Regular security audits** - Continuous monitoring and testing

### Transparency
- **Source citations** - Every answer shows its source
- **Full audit trail** - Track all queries and responses
- **Explainable AI** - Understand how answers are generated
- **Admin controls** - Configure what information is accessible

## 🆘 Support & Resources

### Technical Support
- **Email**: [contact@volentis.ai](mailto:contact@volentis.ai)
- **Website**: [https://volentis.ai](https://volentis.ai)
- **Documentation**: This repository

### Additional Resources
- 📚 [Microsoft identity platform documentation](https://learn.microsoft.com/azure/active-directory/develop/)
- 📚 [Microsoft Graph API documentation](https://learn.microsoft.com/graph/)
- 📚 [SharePoint API documentation](https://learn.microsoft.com/sharepoint/dev/)

### Get Help
- **Integration issues**: Contact Volentis AI support at contact@volentis.ai
- **Microsoft 365 issues**: Consult your tenant administrator
- **Security questions**: Reach out to your organization's security team
- **Book a demo**: Visit [volentis.ai](https://volentis.ai)

## 🤝 About Volentis

**Volentis.ai** builds EU-native AI assistants that act like team members — secure, practical, and GDPR-compliant.

We're advancing teams across:
- 👥 Human Resources
- 🔧 Engineering
- ⚖️ Legal
- 💼 Finance

Our mission is to provide trustworthy, explainable AI that respects European values and data protection standards.

---

## 📞 Contact

**Volentis AI**  
Email: contact@volentis.ai  
Website: https://volentis.ai

---

**Ready to integrate Volentis AI?**  
👉 [Start with the Entra App Registration Guide →](entra-app-registration.md)

---

**Last Updated**: November 25, 2025  
**Version**: 1.0  

*This is technical onboarding documentation for IT administrators. For product information and demos, visit [volentis.ai](https://volentis.ai).*
