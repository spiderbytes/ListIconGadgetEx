# ListIconGadgetEx
A SpiderBasic-Module for additionally ListIconGadget-Functionalities

# Example:

```
IncludeFile "ListIconGadgetEx.sbi"

EnableExplicit

Enumeration
  #Window
  #ListIconGadget
EndEnumeration

Procedure CellClick(ListIconGadget, Column, Row)
  
  Debug "CellClick():"
  Debug "Column: " + Str(Column)
  
  If Row = -1
    Debug "Row: Header"
  Else
    Debug "Row: " + Str(Row)
  EndIf
  
  Debug "------------------"
  
EndProcedure

OpenWindow(#Window, #PB_Ignore, #PB_Ignore, 800, 800, "ListIcon Example", #PB_Window_SystemMenu | #PB_Window_ScreenCentered)
ListIconGadget(#ListIconGadget, 0, 0, 800, 800, "Column 0", 300, #PB_ListIcon_FullRowSelect | #PB_ListIcon_AlwaysShowSelection)

AddGadgetColumn(#ListIconGadget, 1, "Column 1", 400)

; ListIconGadgetEx::SetOddRowColor ("lightgreen", "darkgreen", "black", "white")
; ListIconGadgetEx::SetEvenRowColor("white", "lightblue", "black", "black")

ListIconGadgetEx::SetRowHeight(#ListIconGadget, 36)
ListIconGadgetEx::BindCellClick(#ListIconGadget, @CellClick())

ListIconGadgetEx::SetColumnHeaderAlignment(#ListIconGadget, 0, "center")
ListIconGadgetEx::SetColumnAlignment(#ListIconGadget, 0, "right")

ListIconGadgetEx::SetColumnHeaderAlignment(#ListIconGadget, 1, "right")
ListIconGadgetEx::SetColumnAlignment(#ListIconGadget, 1, "center")

Define Counter

For Counter = 0 To 9
  AddGadgetItem(#ListIconGadget, -1, "Column 0 / Row " + Counter + #LF$ + "Column 1 / Row " + Counter)
Next
```

## License

[MIT](https://github.com/spiderbytes/ListIconGadgetEx/blob/master/LICENSE)
