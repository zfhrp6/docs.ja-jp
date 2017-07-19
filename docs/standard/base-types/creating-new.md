---
title: ".NET Framework における新しい文字列の作成 | Microsoft Docs"
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
  - "Concat メソッド"
  - "CopyTo メソッド"
  - "Format メソッド"
  - "Insert メソッド"
  - "Join メソッド"
  - "文字列 [.NET Framework], 作成"
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# .NET Framework における新しい文字列の作成
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、簡単な代入を使用して文字列を作成できます。また、コンストラクターをオーバーロードして、多数のパラメーターを使用した文字列の作成をサポートすることもできます。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] にも、文字列、文字列配列、またはオブジェクトを結合して新しい文字列オブジェクトを作成するメソッドが <xref:System.String?displayProperty=fullName> クラスに用意されています。  
  
## 代入を使用した文字列の作成  
 新しい <xref:System.String> オブジェクトを作成する最も簡単な方法は、単純にリテラル文字列を <xref:System.String> オブジェクトに割り当てることです。  
  
## クラス コンストラクターを使用した文字列の作成  
 <xref:System.String> クラス コンストラクターのオーバーロードを使用して、文字の配列から文字列を作成できます。  また、特定の文字を指定された数だけ複製して、新しい文字列を作成することもできます。  
  
## 文字列を返すメソッド  
 新しい文字列オブジェクトを返す、便利なメソッドの一覧を次の表に示します。  
  
|メソッド名|使用方法|  
|-----------|----------|  
|<xref:System.String.Format%2A?displayProperty=fullName>|一連の入力オブジェクトから、書式設定された文字列を作成します。|  
|<xref:System.String.Concat%2A?displayProperty=fullName>|2 つ以上の文字列を連結して文字列を作成します。|  
|<xref:System.String.Join%2A?displayProperty=fullName>|文字列の配列を結合して新しい文字列を作成します。|  
|<xref:System.String.Insert%2A?displayProperty=fullName>|既存の文字列内の指定したインデックス位置に文字列を挿入して、新しい文字列を作成します。|  
|<xref:System.String.CopyTo%2A?displayProperty=fullName>|文字の配列内の指定した位置に、文字列内の指定した文字をコピーします。|  
  
### 書式  
 **String.Format** メソッドを使用すると、書式指定された文字列を作成し、複数のオブジェクトを表す文字列を連結できます。  このメソッドは、渡された任意のオブジェクトを文字列に自動変換します。  たとえば、アプリケーションでユーザーに対して **Int32** 値と **DateTime** 値を表示する必要がある場合、これらの値を表す文字列を **Format** メソッドを使用して簡単に作成できます。  このメソッドで使用される書式指定規則の詳細については、[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)に関するセクションを参照してください。  
  
 **Format** メソッドを使用して、整数変数を使用する文字列を作成する例を次に示します。  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 この例では、<xref:System.DateTime.Now%2A?displayProperty=fullName> は現在のスレッドに関連付けられているカルチャで指定される形式で現在の日時を表示します。  
  
### Concat  
 **String.Concat** メソッドを使用すると、2 つ以上の既存のオブジェクトを連結して新しい文字列オブジェクトを簡単に作成できます。  このメソッドは、言語に依存することなく文字列を連結します。  このメソッドは、**System.Object** クラスから派生したすべてのクラスを受け入れます。  既存の 2 つの文字列オブジェクトおよび区切り文字から文字列を作成する例を次に示します。  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### Join  
 **String.Join** メソッドは、文字列の配列と区切り文字から新しい文字列を作成します。  このメソッドは、複数の文字列をコンマなどで区切って連結したリストを作成する場合に便利です。  
  
 文字列の配列を空白で区切って連結する例を次に示します。  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### 挿入  
 **String.Insert** メソッドは、ある文字列を別の文字列内の指定した位置に挿入することによって新しい文字列を作成します。  このメソッドでは、0 から始まるインデックスが使用されます。  文字列を `MyString` 内の 5 番目のインデックス位置に挿入し、挿入した値を含む新しい文字列を作成する例を次に示します。  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### CopyTo  
 **String.CopyTo** メソッドは、文字列の一部を文字配列にコピーします。  文字列のコピー開始位置を示すインデックスと、コピーする文字数の両方を指定できます。  このメソッドには、コピー元のインデックス、文字の配列、コピー先のインデックス、およびコピーする文字数を渡します。  すべてのインデックスは 0 から始まります。  
  
 **CopyTo** メソッドを使用して、文字列オブジェクトに含まれる単語 "Hello" を構成する文字を文字配列の 1 番目のインデックス位置にコピーする例を次に示します。  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## 参照  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)   
 [複合書式指定](../../../docs/standard/base-types/composite-formatting.md)