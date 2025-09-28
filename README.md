# WHMCS PDF Invoice Template - Enterprise Grade

A comprehensive, enterprise-grade PDF invoice template for WHMCS v6/7/8 with advanced features, professional styling, and extensive customization options.

## 🚀 Features

### Core Functionality
- ✅ **WHMCS 6/7/8 Compatibility** - Works across all supported WHMCS versions
- ✅ **Proforma Invoice Support** - Automatic detection and styling for proforma invoices
- ✅ **Status-Aware Rendering** - Different layouts for Paid, Unpaid, Overdue, Refunded invoices
- ✅ **Multi-Currency Support** - Full support for all WHMCS currencies with proper formatting
- ✅ **Dynamic Content** - Intelligent content adaptation based on invoice status and data

### Professional Design
- ✅ **Enterprise Styling** - Modern, professional design with status-based color schemes
- ✅ **Digital Verification Badge** - IT Act 2000 compliant verification system for paid invoices
- ✅ **Status Ribbons** - Visual status indicators with appropriate color coding
- ✅ **Proforma Watermarks** - Diagonal watermarks for proforma invoices
- ✅ **Signature & Stamp Support** - Professional signature and stamp placement

### Advanced Features
- ✅ **Smart Item Parsing** - Intelligent service description parsing with domain and date extraction
- ✅ **Late Fee Handling** - Automatic detection and highlighting of late fee items
- ✅ **Renewal Tracking** - Upcoming renewal dates with urgency indicators
- ✅ **Payment Transactions** - Detailed transaction history on separate page
- ✅ **QR Code Generation** - UPI payment QR codes with invoice-specific data

### Compliance & Legal
- ✅ **Indian Tax Compliance** - GST/CGST/SGST support with proper labeling
- ✅ **TDS Compliance** - Section 194J compliance information
- ✅ **MSME Registration** - UDYAM number display
- ✅ **Legal Terms** - Comprehensive payment terms and legal disclaimers

### Debug & Development
- ✅ **Configurable Debug Mode** - Multiple debug levels for development and troubleshooting
- ✅ **Performance Monitoring** - Built-in performance metrics (development mode)
- ✅ **Variable Inspection** - Complete WHMCS variable inspection and display

## 📋 Installation

### Quick Install
1. Upload `invoicepdf.tpl` to your WHMCS template directory:
   ```
   /templates/twenty-one/invoicepdf.tpl
   ```

2. Ensure required image assets are in place:
   ```
   /assets/img/logo.png (or .jpg)
   /assets/img/sign.png (signature image)
   /assets/img/stamp.png (stamp image)
   ```

3. Configure template settings in the `$ENH` array (see Configuration section)

### Template Structure
```
templates/twenty-one/
├── invoicepdf.tpl          # Main template file
└── assets/img/
    ├── logo.png            # Company logo
    ├── sign.png            # Signature image
    └── stamp.png           # Stamp image
```

## ⚙️ Configuration

### Basic Configuration
Edit the `$ENH` array in the template to customize features:

```php
$ENH = array(
    // Core Status Features
    'show_status_ribbon' => true,
    'show_auth_seal' => true,
    'show_verification_badge' => true,
    
    // Proforma & Invoice Management
    'proforma_enabled' => true,
    'show_original_proforma' => true,
    
    // Payment & Transactions
    'show_transactions' => true,
    'show_payment_ui' => true,
    
    // Compliance & Legal
    'official_auth_seal' => true,
    'show_tax_details' => true,
    'show_client_tax_id' => true,
    'show_company_tax_id' => true,
    
    // Debug & Development
    'show_debug_section' => false,
    'debug_level' => 'full',
    'debug_include_sensitive' => false,
    'debug_show_calculations' => true,
    'debug_show_variables' => true,
    'debug_show_performance' => false
);
```

### Debug Levels
- **minimal**: Basic invoice information only
- **standard**: Basic + Financial + Payment information
- **full**: Standard + Client + Credit information
- **development**: All information + Development metrics

## 🎨 Customization

### Status-Based Styling
The template automatically applies different styling based on invoice status:

- **Paid**: Green accent colors with verification badge
- **Unpaid**: Orange accent colors with payment UI
- **Overdue**: Red accent colors with late fee highlighting
- **Refunded**: Blue accent colors with refund information
- **Proforma**: Special proforma styling with watermarks

### Color Customization
Modify the color constants at the top of the template:

```php
define('COLOR_DARK_GREY', array(64, 64, 64));
define('COLOR_LIGHT_GREY', array(245, 245, 245));
define('COLOR_PURPLE', array(75, 0, 130));
define('COLOR_WHITE', array(255, 255, 255));
define('COLOR_BLACK', array(0, 0, 0));
```

### Company Information
Update company details in the template:

```php
// Company Details Section
$seller_name = isset($companyname) && !empty($companyname) ? $companyname : 'Your Company Name';
$company_address = 'Your Company Address';
$pan_number = 'YOUR_PAN_NUMBER';
$email = 'your-email@company.com';
$phone = '+91 00000 00000';
$msme_number = 'UDYAM-XX-XX-XXXXXXX';
```

### Bank Details
Configure bank information for payment processing:

```php
$bank_details = array(
    'Account Name' => 'Your Company Name',
    'Account Number' => '1234567890',
    'IFSC' => 'BANK0001234',
    'Account Type' => 'Current',
    'Bank' => 'Your Bank Name'
);
```

## 🔧 Advanced Features

### Digital Verification System
The template includes a sophisticated digital verification system for paid invoices:

- **Multi-layered Hash Generation**: SHA-256 + SHA-512 for enhanced security
- **Comprehensive Input Data**: Invoice, client, company, and temporal data
- **Salt-based Security**: Prevents rainbow table attacks
- **IT Act 2000 Compliance**: Legal validity for digital signatures

### Smart Item Parsing
Intelligent parsing of service descriptions:

```php
// Pattern 1: "Service Name - domain.com (date - date)"
// Pattern 2: "Service Name - domain.com - duration"
// Pattern 3: "Service Name (date - date)"
// Pattern 4: "Service Name only"
```

### Renewal Tracking
Automatic renewal date calculation and tracking:

- **Date Extraction**: From service descriptions and duration information
- **Urgency Levels**: Overdue, Urgent (≤30 days), Upcoming (≤90 days)
- **Visual Indicators**: Color-coded urgency levels
- **Renewal Alerts**: Prominent display of upcoming renewals

### Payment QR Codes
Dynamic UPI QR code generation:

- **Paid Invoices**: Generic QR code without amount
- **Unpaid Invoices**: Specific QR code with balance amount
- **Invoice Reference**: Automatic invoice number inclusion
- **Payment Tracking**: Transaction description with invoice details

## 📊 Debug & Troubleshooting

### Enable Debug Mode
Set debug configuration in the `$ENH` array:

```php
$ENH = array(
    'show_debug_section' => true,
    'debug_level' => 'full',
    'debug_include_sensitive' => false,
    'debug_show_calculations' => true,
    'debug_show_variables' => true,
    'debug_show_performance' => false
);
```

### Debug Information Includes
- **Basic Invoice Information**: Status, ID, number, proforma detection
- **Financial Information**: Totals, balance, taxes, credits, discounts
- **Currency & Payment**: Currency settings, payment methods, dates
- **Client Credit**: Available credit, applied credit
- **Performance Metrics**: Generation time, memory usage (development mode)

### Common Issues

#### Template Not Loading
- Check file permissions (644 for template file)
- Verify WHMCS template directory path
- Ensure PHP syntax is correct

#### Images Not Displaying
- Verify image file paths in `/assets/img/`
- Check file permissions (644 for image files)
- Ensure image formats are supported (PNG, JPG)

#### Debug Information Not Showing
- Set `'show_debug_section' => true`
- Choose appropriate debug level
- Check WHMCS error logs

## 🔒 Security Features

### Digital Verification
- **Hash Generation**: SHA-256 + SHA-512 with salt
- **Input Validation**: Comprehensive data validation
- **Timestamp Inclusion**: Temporal verification
- **Legal Compliance**: IT Act 2000 compliance

### Data Protection
- **Sensitive Data**: Configurable sensitive data display
- **Debug Controls**: Separate debug mode for development
- **Access Control**: Template-level access controls

## 📈 Performance

### Optimization Features
- **Dynamic Width Calculation**: Intelligent column width distribution
- **Conditional Rendering**: Only render necessary sections
- **Memory Management**: Efficient memory usage
- **Page Overflow Protection**: Automatic page breaks

### Performance Monitoring
- **Generation Time**: Track template rendering time
- **Memory Usage**: Monitor memory consumption
- **Page Count**: Track multi-page generation
- **Debug Metrics**: Detailed performance analysis

## 🛠️ Development

### Template Structure
```
Template Sections:
├── Page Setup & Initialization
├── Header Section (Logo & Title)
├── Status Ribbon & Verification Badge
├── Invoice Details Section
├── Billed To/By Sections
├── Itemized Table
├── Totals Section
├── Signature & Stamp Section
├── Bottom Sections (Terms, Bank, UPI)
├── Compliance & Legal Section
└── Last Page (Renewals, Transactions, Debug)
```

### Adding Custom Features
1. **New Status Types**: Add to `$status_colors` array
2. **Custom Fields**: Extend client details section
3. **Additional Totals**: Add to totals calculation section
4. **New Debug Info**: Extend debug information display

### Testing
- **Status Testing**: Test all invoice statuses
- **Currency Testing**: Test with different currencies
- **Debug Testing**: Verify debug information accuracy
- **Performance Testing**: Monitor generation time and memory usage

## 📝 Changelog

### Version 2.0.0
- ✅ Complete rewrite with enterprise-grade features
- ✅ Digital verification system implementation
- ✅ Smart item parsing and renewal tracking
- ✅ Status-aware rendering and styling
- ✅ Comprehensive debug system
- ✅ Indian tax compliance features
- ✅ UPI QR code generation
- ✅ Professional signature and stamp support

### Version 1.0.0
- ✅ Basic WHMCS invoice template
- ✅ Standard invoice layout
- ✅ Basic customization options

## 🤝 Support

### Documentation
- **Template Comments**: Extensive inline documentation
- **Configuration Guide**: Detailed configuration options
- **Debug Guide**: Comprehensive debugging information
- **Customization Examples**: Code examples for common modifications

### Troubleshooting
1. **Check Debug Mode**: Enable debug mode for detailed information
2. **Verify Configuration**: Ensure all settings are correct
3. **Check WHMCS Logs**: Review WHMCS error logs
4. **Test with Sample Data**: Use test invoices for debugging

### Common Solutions
- **Template Not Loading**: Check file permissions and syntax
- **Images Missing**: Verify image file paths and permissions
- **Debug Not Working**: Ensure debug mode is enabled
- **Styling Issues**: Check color constants and configuration

## 📄 License

This template is provided as-is for WHMCS installations. Please ensure compliance with your WHMCS license and local regulations.

## 🔗 Related Files

- **WHMCS Template System**: [WHMCS Documentation](https://docs.whmcs.com/Template_Syntax)
- **TCPDF Library**: [TCPDF Documentation](https://tcpdf.org/docs/)
- **Indian Tax Compliance**: [GST Guidelines](https://www.gst.gov.in/)

---

**Template Version**: 2.0.0  
**WHMCS Compatibility**: 6.0+ (Tested on 6.3, 7.10, 8.13)  
**PHP Compatibility**: 5.6+ (Tested on 5.6, 7.0, 7.4, 8.0, 8.1, 8.2)  
**Last Updated**: 2025-01-28
