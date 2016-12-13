When importing, activerecord-import does not update counter cache columns on its own. You will need to do one of the following:
* Provide values for the counter cache column
* Update them manually