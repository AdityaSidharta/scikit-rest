Module scikit_rest
==================
Automatically serve ML model as a REST API

Sub-modules
-----------
* scikit_rest.resource
* scikit_rest.types
* scikit_rest.validator

Functions
---------

    
`infer(input_df)`
:   Automatically infer the column list and column types from the input DataFrame
    
    Args:
        input_df: DataFrame, where the column list and column types will be inferred from.
    
    Returns:
        col_list: List of Column names, where the order of the values will dictate the order within the pandas DataFrame
        col_types: Dictionary of Column Names and the type of the variable, used for input Validation. If the values
        of the dictionary is instead a list, We assume that any input for the variable can only be any of
         the ones listed within the list

    
`serve(col_list, col_types, transform_fn, predict_fn, port=1234, is_nullable=False, name='model')`
:   Setting up ML model as a REST API server
    
    Args:
        col_list: List of Column names, where the order of the values will dictate the order within the pandas DataFrame
        col_types: Dictionary of Column Names and the type of the variable, used for input Validation. If the values
        of the dictionary is instead a list, We assume that any input for the variable can only be any of
         the ones listed within the list
        transform_fn: Function which convert the input dataframe into test dataframe,
        where we can call model.predict upon to get the final result
        predict_fn: Function which convert the test dataframe into result. If a ML model instance is passed in, we will
        instead try to call model.predict_proba / model.predict to get the result
        port: Port Number where the REST API should be served upon
        is_nullable: Whether input API can be nullable
        name: Name of the program
