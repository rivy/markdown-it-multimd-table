# MultiMarkdown Tables: Other Notes
From [MultiMarkdown 5](http://fletcher.github.io/MultiMarkdown-5)

## Standards

```markdown
First Header  | Second Header | Third Header |
------------  | :-----------: | -----------: |
Content       |   **Cell**    |         Cell |
New section   |     More      |         Data |
```
```html
<table>
<thead>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
<tr>
<td>New section</td>
<td style="text-align:center">More</td>
<td style="text-align:right">Data</td>
</tr>
</tbody>
</table>
```

## It is optional whether you have | characters at the beginning and end of lines.
> NOTE: Defined in PHP Markdown Extra. Test cases ignored.

## The “separator” line uses ---- or ==== to indicate the line between a header and cell. The length of the line doesn’t matter, but must have at least one character per cell.

```markdown
First Header  | Second Header | Third Header |
============  | ::+           | -----------: |
Content       |   **Cell**    |         Cell |
New section   |     More      |         Data |
```
```html
<p>First Header  | Second Header | Third Header |
============  | ::+           | -----------: |
Content       |   <strong>Cell</strong>    |         Cell |
New section   |     More      |         Data |</p>
```

## To set alignment, you can use a colon to designate left or right alignment, or a colon at each end to designate center alignment, as above. If no colon is present, the default alignment of your system is selected (left in most cases). If the separator line ends with +, then cells in that column will be wrapped when exporting to LaTeX if they are long enough.

```markdown
First Header  | Second Header | Third Header |
============  | :==========:+ | -----------: |
Content       |   **Cell**    |         Cell |
New section   |     More      |         Data |
```
```html
<table>
<thead>
<tr>
<th>First Header</th>
<th style="text-align:center" class="extend">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" class="extend"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
<tr>
<td>New section</td>
<td style="text-align:center" class="extend">More</td>
<td style="text-align:right">Data</td>
</tr>
</tbody>
</table>
```

## To indicate that a cell should span multiple columns, then simply add additional pipes (|) at the end of the cell, as shown in the example. If the cell in question is at the end of the row, then of course that means that pipes are not optional at the end of that row…. The number of pipes equals the number of columns the cell should span.

```markdown
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |
```
```html
<table>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" colspan="2"><em>Long Cell</em></td>
</tr>
<tr>
<td>Content</td>
<td style="text-align:center"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
</tbody>
</table>
```

```markdown
|             |          Grouping           ||
 ------------ | :-----------: | -----------: |
|          *Long Cell*       ||
|                                          |||         Cell |
```
```html
<table>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2"><em>Long Cell</em></td>
<td style="text-align:right"></td>
</tr>
<tr>
<td colspan="3"></td>
</tr>
</tbody>
</table>
```
## You can use normal Markdown markup within the table cells.
> NOTE: From Definitions of PHP Markdown Extra, "normal" means "inline". If in this case, test cases are ignored.

## Captions are optional, but if present must be at the beginning of the line immediately preceding or following the table, start with [, and end with ]. If you have a caption before and after the table, only the first match will be used.
> NOTE: Assumed that caption has higher priority than table content, as the next example

```markdown
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |
[             |               |              ]
```
```html
<table>
<caption id="">             |               |              </caption>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" colspan="2"><em>Long Cell</em></td>
</tr>
<tr>
<td>Content</td>
<td style="text-align:center"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
</tbody>
</table>
```

```markdown
[Prototype table]
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |
[Prototype table caption]
```
```html
<table>
<caption id="prototypetable">Prototype table</caption>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" colspan="2"><em>Long Cell</em></td>
</tr>
<tr>
<td>Content</td>
<td style="text-align:center"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
</tbody>
</table>
```

## If you have a caption, you can also have a label, allowing you to create anchors pointing to the table. If there is no label, then the caption acts as the label

```markdown
[Prototype table][label1]
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |
[Prototype table caption][label2]
```
```html
<table>
<caption id="label1">Prototype table</caption>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" colspan="2"><em>Long Cell</em></td>
</tr>
<tr>
<td>Content</td>
<td style="text-align:center"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
</tbody>
</table>
```

## Cells can be empty.
> Assumed must with pipe characters on its both side

```markdown
|             |                             ||
|             | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |                             ||
|             |               |         Cell |
[Prototype table]
```
```html
<table>
<caption id="prototypetable">Prototype table</caption>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2"></th>
</tr>
<tr>
<th></th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" colspan="2"></td>
</tr>
<tr>
<td></td>
<td style="text-align:center"></td>
<td style="text-align:right">Cell</td>
</tr>
</tbody>
</table>
```

## You can create multiple <tbody> tags (for HTML) within a table by having a single empty line between rows of the table. This allows your CSS to place horizontal borders to emphasize different sections of the table. This feature doesn’t work in all output formats (e.g. RTF and OpenDocument).
> NOTE: any empty tbody is not allowed

```markdown
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |

New section   |     More      |         Data |
And more      | With an escaped '\|'         ||  
[Prototype table]
```
```html
<table>
<caption id="prototypetable">Prototype table</caption>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content</td>
<td style="text-align:center" colspan="2"><em>Long Cell</em></td>
</tr>
<tr>
<td>Content</td>
<td style="text-align:center"><strong>Cell</strong></td>
<td style="text-align:right">Cell</td>
</tr>
</tbody>
<tbody>
<tr>
<td>New section</td>
<td style="text-align:center">More</td>
<td style="text-align:right">Data</td>
</tr>
<tr>
<td>And more</td>
<td style="text-align:center" colspan="2">With an escaped '|'</td>
</tr>
</tbody>
</table>
```

```markdown
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |

Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |

New section   |     More      |         Data |
And more      | With an escaped '\|'         ||  
[Prototype table]
```
```html
<table>
<caption id="prototypetable">Prototype table</caption>
<thead>
<tr>
<th></th>
<th style="text-align:center" colspan="2">Grouping</th>
</tr>
<tr>
<th>First Header</th>
<th style="text-align:center">Second Header</th>
<th style="text-align:right">Third Header</th>
</tr>
</thead>
<tbody></tbody>
</table>
<p>Content       |          <em>Long Cell</em>        ||
Content       |   <strong>Cell</strong>    |         Cell |</p>
<p>New section   |     More      |         Data |
And more      | With an escaped '|'         ||<br>
[Prototype table]</p>
```