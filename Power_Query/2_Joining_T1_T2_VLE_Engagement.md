```
let
    Merged = Table.NestedJoin(T1, {"STUDENT_ID"}, T2, {"STUDENT_ID"}, "T2_Data", JoinKind.LeftOuter),
    #"Expanded T2" = Table.ExpandTableColumn(
        Merged,
        "T2_Data",
        List.RemoveItems(Table.ColumnNames(T2), {"STUDENT_ID"}),
        List.RemoveItems(Table.ColumnNames(T2), {"STUDENT_ID"})
    )
in
    #"Expanded T2"
```