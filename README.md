# Xl2Collection - Power FX Formula Generator

**Xl2Collection** is a web tool that generates Power FX formulas to import Excel data (TSV format) into Power Apps collections. It automatically detects column types, handles complex headers, and supports unpivot transformations.

## 🚀 Features

### ✨ Smart Analysis
- **Automatic type detection**: Value, DateValue, DateTimeValue, Text
- **Complex header parsing**: Handles multiline headers and quoted cells
- **Sample preview**: Displays first data row for each column
- **Column selection**: Choose which columns to include via checkboxes

### 🔄 Unpivot Transformation
- **Unpivot mode**: Transform multiple columns into attribute/value pairs
- **Mixed columns**: Combine key columns with unpivoted columns
- **Customizable names**: Define your own attribute and value column names
- **Flat output**: Generates properly flattened rows in the collection

### 🌍 International Support
- **Bilingual interface**: 🇺🇸 English / 🇫🇷 French
- **Adaptive Power FX syntax**:
  - **EN**: Comma list separator `,`, semicolon instruction separator `;`, decimal point `.`
  - **FR**: Semicolon list separator `;`, double semicolon instruction separator `;;`, decimal comma `,`

### 📋 Generated Formula
- **Ready to use**: Complete formula with proper syntax for your language
- **Easy customization**: Single point to replace (`input_data` variable)
- **Well commented**: Clear explanations of each step
- **Copy to clipboard**: One-click copy button

## 📖 How to Use

### 1. Import Excel Data
1. In Excel, select your data (header + a few data rows)
2. Copy (Ctrl+C)
3. Click **"Import Excel"** button
4. Paste into the textarea (Ctrl+V)
5. Click **"Analyze and close"**

### 2. Configure Columns
- **Checked**: Select which columns to include in the collection
- **Unpivot**: Mark columns to transform into attribute/value pairs
- **DType**: Adjust data type if auto-detection is incorrect

### 3. Customize Unpivot (if applicable)
- Set **attribute column name** (default: "Attribute")
- Set **value column name** (default: "Value")

### 4. Copy Formula
1. Click the **"Copy"** button
2. Paste into the `OnSelect` event of your Power Apps import button
3. Replace `TextInputPaste.Text` with your actual control or variable

## 🎯 Use Cases

### Simple Import
Import an Excel table with selected columns into a Power Apps collection.

**Example**: Customer list with Name, Email, Phone, City
- All columns checked
- No unpivot
- Result: Collection with 4 columns

### Unpivot for Reporting
Transform monthly columns into rows for easier visualization.

**Example**: Sales data with Year, Product, Jan, Feb, Mar, Apr...
- Key columns: Year, Product (checked, not unpivoted)
- Data columns: Jan, Feb, Mar, Apr... (checked AND unpivoted)
- Result: Collection with Year, Product, Month (attribute), Sales (value)

## 🔧 Technical Details

### Input Format
- **Separator**: TAB (standard Excel copy format)
- **Headers**: Supports multiline and quoted headers
- **Encoding**: Handles CR/LF normalization

### Generated Formula Structure
```powerfx
With(
    {
        // Replace input_data with your control or variable
        input_data: TextInputPaste.Text
    };
    With(
        {
            // Normalize CR/LF and extract body (skip header)
            _txt: Mid(...)
        };
        // Load colData
        ClearCollect(
            colData;
            ForAll(...)
        )
    )
)
```

### Power FX Syntax Adaptation
The tool automatically adapts the formula syntax based on the selected language:

| Element | English (EN) | French (FR) |
|---------|--------------|-------------|
| List separator | `,` | `;` |
| Instruction separator | `;` | `;;` |
| Decimal separator | `.` | `,` |

**Example**:
- EN: `Index(_cells, 1).Value`
- FR: `Index(_cells; 1).Value`

## 📦 Deployment

Single HTML file - no dependencies required. Just open in a browser and use!

## 📄 License

Open source - Free to use and modify

## Credits

www.linkedin.com/in/julien-quemere

**Xl2Collection** - Transform Excel data into Power Apps collections with ease! ⚡
