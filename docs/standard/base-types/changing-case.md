---
title: ".NET Framework における大文字と小文字の変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "大文字と小文字の区別"
  - "小文字"
  - "文字列 [.NET Framework], case"
  - "ToLower メソッド"
  - "ToUpper メソッド"
  - "大文字"
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# .NET Framework における大文字と小文字の変更
ユーザーからの入力を受け付けるアプリケーションを記述する場合、ユーザーがデータ入力に使用するケースを正確に予測することはできません。  多くの場合、特にユーザー インターフェイスにそれを表示する場合には、文字列に一貫性のあるケースを使用することが求められます。  次の表は、3 つのケース変更方式を示しています。  最初の 2 つの方式は、カルチャを受け入れるオーバーロードを提供します。  
  
|メソッド名|用途|  
|-----------|--------|  
|<xref:System.String.ToUpper%2A?displayProperty=fullName>|文字列内のすべての文字を大文字に変換します。|  
|<xref:System.String.ToLower%2A?displayProperty=fullName>|文字列内のすべての文字を小文字に変換します。|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=fullName>|文字列をタイトル ケースに変換します。|  
  
> [!WARNING]
>  <xref:System.String.ToUpper%2A?displayProperty=fullName> と <xref:System.String.ToLower%2A?displayProperty=fullName> の方式を使用して、文字列を比較したり等しいかどうかをテストしたりする目的で、それらの文字列を変換するべきではないことに注意してください。  詳しくは、「[大小混合文字の文字列を比較する](#Comparing)」セクションを参照してください。  
  
<a name="Comparing"></a>   
## 大小混合文字の文字列を比較する  
 大小混合文字の文字列を比較してそれらの順序を判別するには、`comparisonType` パラメーターのある <xref:System.String.CompareTo%2A?displayProperty=fullName> メソッドのいずれかのオーバーロードを呼び出して、`comparisonType` 引数に <xref:System.StringComparison?displayProperty=fullName>、<xref:System.StringComparison?displayProperty=fullName>、または <xref:System.StringComparison?displayProperty=fullName> の値を指定します。  現在のカルチャ以外の特定のカルチャを使用して比較する場合、`culture` と `options` の両方のパラメーターのある <xref:System.String.CompareTo%2A?displayProperty=fullName> メソッドのオーバーロードを呼び出して、`options` 引数に <xref:System.Globalization.CompareOptions?displayProperty=fullName> の値を指定します。  
  
 大小混合文字の文字列を比較してそれらが等しいかどうかを判別するには、`comparisonType` パラメーターのある <xref:System.String.Equals%2A?displayProperty=fullName> メソッドのいずれかのオーバーロードを呼び出して、`comparisonType` 引数に <xref:System.StringComparison?displayProperty=fullName>、<xref:System.StringComparison?displayProperty=fullName>、または <xref:System.StringComparison?displayProperty=fullName> の値を指定します。  
  
 詳しくは、「[文字列を使用するためのベスト プラクティス](../../../docs/standard/base-types/best-practices-strings.md)」を参照してください。  
  
## ToUpper  
 <xref:System.String.ToUpper%2A?displayProperty=fullName> メソッドは文字列内のすべての文字を大文字に変換します。  次の例では、文字列 "Hello World\!" を大小混合文字から大文字に変換します。  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 前の例は、既定でカルチャに依存しています。これには、現在のカルチャのケース表記規則が適用されます。  カルチャに依存しないケース変更を実行したり、特定のカルチャのケース表記規則を適用したりするには、<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=fullName> メソッドのオーバーロードを使用して、*culture* パラメーターに指定のカルチャを表す <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo?displayProperty=fullName> オブジェクトの値を提供します。  <xref:System.String.ToUpper%2A> メソッドを使用してカルチャに依存しないケース変更を実行する方法を示す例については、「[カルチャを認識しない大文字と小文字の変更の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)」を参照してください。  
  
## ToLower  
 <xref:System.String.ToLower%2A?displayProperty=fullName> メソッドは、前のメソッドと似ていますが、代わりに文字列内のすべての文字を小文字に変換します。  次の例では、文字列 "Hello World\!" を小文字に変換します。  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 前の例は、既定でカルチャに依存しています。これには、現在のカルチャのケース表記規則が適用されます。  カルチャに依存しないケース変更を実行したり、特定のカルチャのケース表記規則を適用したりするには、<xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=fullName> メソッドのオーバーロードを使用して、*culture* パラメーターに指定のカルチャを表す <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo?displayProperty=fullName> オブジェクトの値を提供します。  <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> メソッドを使用してカルチャに依存しないケース変更を実行する方法を示す例については、「[カルチャを認識しない大文字と小文字の変更の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)」を参照してください。  
  
## ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=fullName> は、各単語の最初の文字を大文字に変換し、残りの文字を小文字に変換します。  ただし、すべて大文字である単語は頭字語であると想定されて、変換されません。  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=fullName> メソッドはカルチャに依存しています。つまり、特定のカルチャのケース表記規則を使用します。  メソッドを呼び出すためには、最初に特定のカルチャのケース表記規則を表す <xref:System.Globalization.TextInfo> オブジェクトを、特定のカルチャの <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=fullName> プロパティから取得します。  
  
 次の例は、配列内の各文字列を <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=fullName> メソッドに渡します。  文字列には、適切なタイトルの文字列と頭字語が含まれています。  文字列は、英語 \(米国\) カルチャのケース表記規則を使用して、タイトル ケースに変換されます。  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 カルチャに依存していても、<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=fullName> メソッドは言語的に正しい大文字小文字の規則を提供しないことに注意してください。  たとえば、前の例で、メソッドは "a tale of two cities" を "A Tale Of Two Cities" に変換します。  しかし、en\-US カルチャで言語的に正しいタイトルの大文字小文字の表記は "A Tale of Two Cities" です。  
  
## 参照  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)   
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)