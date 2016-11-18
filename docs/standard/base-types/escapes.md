---
title: "正規表現での文字のエスケープ"
description: "正規表現での文字のエスケープ"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 41d35531-2af9-47d4-9780-fbc1e682fbc2
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e4f4b9cde90a98215c0aaab6da217ff68476cf88

---

# <a name="character-escapes-in-regular-expressions"></a>正規表現での文字のエスケープ

正規表現の円記号 (\)) は、次のいずれかを示します。 

* 後に続く文字が、次のセクションの表に示す特殊文字であること。 たとえば、**\b** は、正規表現の一致がワード境界から開始する必要があることを示すアンカーであり、**\t** はタブを表します。**\x020** は空白を表します。

* エスケープされていない言語構成要素として解釈される文字は、文字どおりに解釈する必要があること。 たとえば、中かっこ (**{**) は量指定子の定義を開始しますが、円記号とそれに続く中かっこ (**\{**) は、正規表現エンジンで中かっこに一致させる必要があることを示します。 同様に、1 つの円記号はエスケープされた言語構成要素の開始を示しますが、2 つの円記号 (**\\**) は、正規表現エンジンで円記号に一致させる必要があることを示します。

> [!NOTE]
> 文字エスケープは、正規表現では認識されますが、置換パターンでは認識されません。 
 
## <a name="character-escapes-in-net"></a>.NET での文字のエスケープ

次の表は、.NET の正規表現でサポートされている文字エスケープの一覧です。

文字または文字シーケンス | 説明
--------------------- | ----------- 
次の文字を除くすべての文字: **. $ ^ { [ ( &#124; ) * + ? \** | **文字またはシーケンス**の列にリストされているもの以外の文字は、正規表現で特別な意味を持ちません。それらは、その文字自体と一致します。 **文字またはシーケンス**の列に含まれる文字は、特殊な正規表現言語要素です。 正規表現でそれらの文字と一致するためには、エスケープするか、正の文字グループに含める必要があります。 たとえば、正規表現の `\$\d+ or [$]\d+` は "$1200" と一致します。 
**\a** | ビープ音文字の **\u0007** と一致します。
**\b** | __[__*character*_*group*__]__ 文字クラスでバックスペース **\u0008** と一致します。 (「[正規表現での文字クラス](classes.md)」を参照してください)。文字クラスの外部では、**\b** はワード境界と一致するアンカーです。 (「[正規表現のアンカー](anchors.md)」を参照してください。)
**\t** | タブの **\u0009** と一致します。
**\r** | キャリッジ リターンの **\u000D** と一致します。 **\r** の機能は **\n** という改行文字と同じではありません。
**\v** | 垂直タブの **\u000B** と一致します。
**\f** | フォーム フィードの **\u000C** と一致します。
**\n** | 改行文字の **\u000A** と一致します。
**\e** | エスケープ文字の **\u001B** と一致します。
**\**_nnn_ | ASCII 文字と一致します。nnn は、8 進文字コードを表す 2 桁または 3 桁で構成されます。 たとえば、`\040` は、空白文字を表します。 この構成体は、1 桁のみの場合 (`\2` など)、またはキャプチャ グループの番号に対応する場合には前方参照として解釈されます。 (「[正規表現での前方参照構成体](backreference.md)」を参照してください)。 
**\x**_nn_ | ASCII 文字と一致します。*nn* は 2 桁の 16 進文字コードです。
**\c**_X_ | ASCII の制御文字と一致します。*X* は制御文字です。 たとえば、`\cC` は CTRL-C です。
**\u**_nnnn_ | 値が *nnnn* の 16 進数である UTF-16 コード単位と一致します。 **注:** .NET では、Unicode を指定するために使用する Perl5 の文字エスケープはサポートされません。 Perl 5 の文字エスケープのフォームは **\x{###...}** となります。**####…** は、 一連の 16 進数です。 代わりに、**\u**_nnnn_ を使用します。 
**\** | エスケープ文字として認識されない文字が後ろに付いている場合は、その文字と一致します。 たとえば、`\*` はアスタリスク (*) と一致し、`\x2A` と同じです。
 
## <a name="example"></a>例

正規表現の文字エスケープの使用例を次に示します。 2009 年の世界最大規模の都市の名前と人口を含む文字列を解析します。 個々の都市の名前は、タブ (**\t**) または縦棒 (| または `\u007c`) で人口から区切られます。 個々の都市とその人口は、復帰とライン フィードで互いに区切られています。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string delimited = @"\G(.+)[\t\u007c](.+)\r?\n";
      string input = "Mumbai, India|13,922,125\t\n" + 
                            "Shanghai, China\t13,831,900\n" + 
                            "Karachi, Pakistan|12,991,000\n" + 
                            "Delhi, India\t12,259,230\n" + 
                            "Istanbul, Turkey|11,372,613\n";
      Console.WriteLine("Population of the World's Largest Cities, 2009");
      Console.WriteLine();
      Console.WriteLine("{0,-20} {1,10}", "City", "Population");
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, delimited))
         Console.WriteLine("{0,-20} {1,10}", match.Groups[1].Value, 
                                            match.Groups[2].Value);
   }
}
// The example displyas the following output:
//       Population of the World's Largest Cities, 2009
//       
//       City                 Population
//       
//       Mumbai, India        13,922,125
//       Shanghai, China      13,831,900
//       Karachi, Pakistan    12,991,000
//       Delhi, India         12,259,230
//       Istanbul, Turkey     11,372,613
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim delimited As String = "\G(.+)[\t\u007c](.+)\r?\n"
      Dim input As String = "Mumbai, India|13,922,125" + vbCrLf + _
                            "Shanghai, China" + vbTab + "13,831,900" + vbCrLf + _
                            "Karachi, Pakistan|12,991,000" + vbCrLf + _
                            "Delhi, India" + vbTab + "12,259,230" + vbCrLf + _
                            "Istanbul, Turkey|11,372,613" + vbCrLf
      Console.WriteLine("Population of the World's Largest Cities, 2009")
      Console.WriteLine()
      Console.WriteLine("{0,-20} {1,10}", "City", "Population")
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, delimited)
         Console.WriteLine("{0,-20} {1,10}", match.Groups(1).Value, _
                                            match.Groups(2).Value)
      Next                         
   End Sub
End Module
' The example displays the following output:
'       Population of the World's Largest Cities, 2009
'       
'       City                 Population
'       
'       Mumbai, India        13,922,125
'       Shanghai, China      13,831,900
'       Karachi, Pakistan    12,991,000
'       Delhi, India         12,259,230
'       Istanbul, Turkey     11,372,613
```

この正規表現 `\G(.+)[\t|\u007c](.+)\r?\n` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`\G` | 最後の一致の終了位置から照合を開始します。
`(.+)` | 任意の文字と 1 回以上、一致します。 これが最初のキャプチャ グループです。
`[\t\u007c]` | タブ (**\t**) または縦棒 (&#124;) と一致します。
`(.+)` | 任意の文字と 1 回以上、一致します。 これが 2 番目のキャプチャ グループです。
`\r?\n` | 復帰とそれに続く改行に、0 回または 1 回一致します。
 
## <a name="see-also"></a>関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)




<!--HONumber=Nov16_HO3-->


