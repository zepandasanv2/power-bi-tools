# Power Query (M)

A collection of reusable Power Query (M) scripts for data transformation and preparation in Power BI.

## Available Scripts

### 1. YYYYMMDDHHMMSS to DateTime

**File:** [datetime-from-yyyymmddhhmmss.m](datetime-from-yyyymmddhhmmss.m)

#### Description

Converts a 14-digit timestamp in `yyyyMMddHHmmss` format into a Power Query `datetime` value using the native `DateTime.FromText()` function.

#### Example

| Input | Output |
|---|---|
| `20261013153045` | `2026-10-13 15:30:45` |
| `20250108094512` | `2025-01-08 09:45:12` |
| `20261231235959` | `2026-12-31 23:59:59` |

#### Usage

1. Open **Power Query Editor** in Power BI.
2. Select **Add Column → Custom Column**.
3. Copy the code from the `.m` file.
4. Replace `[DateColumn]` with your source column name.
5. Set the resulting column's data type to **Date/Time**, if necessary.

#### How It Works

- `Text.From()` converts the input into text.
- `DateTime.FromText()` converts the formatted text into a datetime value.
- `Format = "yyyyMMddHHmmss"` specifies the expected timestamp structure.
- `Culture = "en-US"` specifies the US English locale.

#### Notes

- The input must contain a valid timestamp in `yyyyMMddHHmmss` format.
- Invalid or incomplete timestamps may produce errors.
- Null values are not explicitly handled.
- The resulting datetime does not include timezone information.