# DataManager R6 Class for Shiny Modules

An R6 class to manage data loading, preprocessing, and common UI
elements for various Shiny modules in the package. It handles file
reading (csv, xlsx, sav, sas7bdat, dta), initial variable analysis, and
the rendering and logic for common data manipulations like creating
binary variables, changing factor references, and subsetting data. This
class is designed to be used internally by other Shiny server modules to
reduce code duplication.

## Public fields

- `input`:

  Shiny module's input object.

- `output`:

  Shiny module's output object.

- `session`:

  Shiny module's session object.

- `ns`:

  Shiny module's namespace function.

- `nfactor.limit`:

  The threshold for unique values to suggest a numeric variable as a
  factor.

- `initial_data_info`:

  A reactive value holding the initially loaded data and its metadata.

- `processed_data`:

  A reactive value holding the data after all transformations have been
  applied.

## Methods

### Public methods

- [`DataManager$new()`](#method-DataManager-new)

- [`DataManager$get_reactive_data()`](#method-DataManager-get_reactive_data)

- [`DataManager$clone()`](#method-DataManager-clone)

------------------------------------------------------------------------

### Method [`new()`](https://rdrr.io/r/methods/new.html)

Create a new DataManager object.

#### Usage

    DataManager$new(input, output, session, nfactor.limit = 20)

#### Arguments

- `input`:

  Shiny module's input object.

- `output`:

  Shiny module's output object.

- `session`:

  Shiny module's session object.

- `nfactor.limit`:

  The maximum number of unique values for a continuous variable to be
  suggested as a factor.

#### Returns

A new \`DataManager\` object.

------------------------------------------------------------------------

### Method `get_reactive_data()`

Returns the final processed data as a reactive expression. This is the
main output to be used by the calling module.

#### Usage

    DataManager$get_reactive_data()

#### Returns

A reactive expression that returns a list containing the processed
\`data\`, \`label\` information, and \`naomit\` message.

------------------------------------------------------------------------

### Method `clone()`

The objects of this class are cloneable with this method.

#### Usage

    DataManager$clone(deep = FALSE)

#### Arguments

- `deep`:

  Whether to make a deep clone.
