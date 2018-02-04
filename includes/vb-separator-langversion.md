
<span data-ttu-id="64914-101">先行する区切り記号としてアンダー スコア文字を使用するには、Visual Basic プロジェクトに次の要素を追加する必要があります (\*.vbproj) ファイル。</span><span class="sxs-lookup"><span data-stu-id="64914-101">To use the underscore character as a leading separator, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```
