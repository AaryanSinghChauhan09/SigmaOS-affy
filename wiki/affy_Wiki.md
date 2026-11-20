# SigmaOS-affy Component Wiki

## Overview
SigmaOS-affy provides bioinformatics and Affymetrix microarray analysis support for the SigmaOS operating system. It demonstrates the data analysis subsystem and bioinformatics tools within the SigmaOS ecosystem, following the principles of clear abstraction and deterministic bioinit initialization.

## Principles
- Single Responsibility
- Bioinformatics Abstraction
- Fail-Fast on Bioinformatics Initialization Errors
- Deterministic Bioinformatics Setup
- Clear Abstraction Over Bioinformatics APIs
- Composition over Inheritance for bioinformatics extensions

## Architecture
SigmaOS-affy follows a bioinformatics pattern:
- **Analysis Core**: Provides microarray data processing, gene expression analysis, and statistical computing
- **Affymetrix Support**: Supports Affymetrix array format parsing and chip type detection
- **Result Visualization**: Supports data visualization and result reporting
- **Error Handling**: Fail-fast on invalid bioinformatics configurations or unsupported data types

## API
The component provides the following public APIs:
- `bio::microarray::parse(path)` - Parse Affymetrix microarray data file
- `bio::expression::analyze(data)` - Analyze gene expression data
- `bio::statistics::test(data, test_type)` - Perform statistical tests on biological data
- `bio::result::visualize(data)` - Visualize analysis results and export figures
- Error types for bioinformatics failure scenarios or unsupported data types

## Test Structure (Arrange-Act-ASSERT)
All tests follow the AAA pattern:
1. **Arrange**: Set up test environment with specific bioinformatics configuration
2. **Act**: Execute the code under test (data parsing, expression analysis)
3. **Assert**: Verify the expected bioinformatics results

Example:
```rust
#[test]
fn test_bio_parse_aaa() {
    // Arrange
    let data_path = "/data/test-affy.chip";
    
    // Act
    let result = bio::microarray::parse(data_path);
    
    // Assert
    assert!(result.is_ok());
    let chip = result.unwrap();
    assert!(chip.is_valid());
}
```

## Development
- Follows Rust best practices with `#![forbid(unsafe_code)]`
- Bioinformatics initialization is best-effort; gracefully degrades on unsupported configurations
- Comprehensive error types for all bioinformatics failure scenarios
- Unit tests provided for microarray parsing and expression analysis
- Integration tests for full bioinformatics subsystem with actual microarray data

## TODO
- Add support for additional array formats (Illumina, Agilent)
- Expand expression analysis capabilities ( differential expression, pathway analysis)
- Add statistical test support (t-test, ANOVA, chi-squared)
- Create integration tests with actual microarray data samples
- Implement result persistence and analysis history features