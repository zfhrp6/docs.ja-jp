---
title: "列挙型書式指定文字列 | Microsoft Docs"
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
  - "列挙型書式指定文字列"
  - "書式指定子, 列挙型書式指定文字列"
  - "書式指定 [.NET Framework], 列挙型"
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 列挙型書式指定文字列
<xref:System.Enum.ToString%2A?displayProperty=fullName> メソッドを使用すると、列挙型のメンバーの数値、16 進数値、または文字列値を表す新しい文字列オブジェクトを作成できます。  `ToString` メソッドでは、返す値を指定するために列挙型書式指定文字列が使用されます。  
  
 列挙型書式指定文字列と、各書式指定文字列が返す値の一覧を次の表に示します。  列挙型書式指定子では、大文字と小文字は区別されません。  
  
|書式指定文字列|結果|  
|-------------|--------|  
|G または g|列挙型エントリを文字列値として表示できる場合は、文字列値として表示されます。文字列値として表示できない場合には、現在のインスタンスの整数値が表示されます。  **Flags** 属性が設定されており、これによって列挙型が定義されている場合には、有効な各エントリの文字列値がコンマで区切られた形式で連結されます。  **Flags** 属性が設定されていない場合には、無効な値が数値エントリとして表示されます。  G 書式指定子の例を次に示します。<br /><br /> [!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
 [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]|  
|F または f|列挙エントリを文字列値として表示できる場合には、文字列値として表示されます。  **Flags** 属性がない場合でも、列挙値の各エントリの合計値として値を完全に表示できる場合には、有効な各エントリの文字列値が、コンマで区切った形式で連結されます。  列挙エントリによって値を完全に決定できない場合は、この値は整数値として書式指定されます。  F 書式指定子の例を次に示します。<br /><br /> [!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
 [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]|  
|D または d|列挙エントリが、表現可能な最も短い整数値として表示されます。  D 書式指定子の例を次に示します。<br /><br /> [!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
 [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]|  
|X または x|列挙エントリが 16 進数値として表示されます。  最小桁数である 8 桁で値を表示するため、必要に応じて先行ゼロが埋め込まれます。  X 書式指定子の例を次に示します。<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
 [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]|  
  
## 例  
 `Red`、`Blue`、および `Green` の 3 つのエントリから成る `Colors` という列挙型を定義する例を次に示します。  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 列挙値の定義が完了したら、次の方法でインスタンスを宣言できます。  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 その後、`Color.ToString(System.String)` メソッドを使用して、それに渡される書式指定子に応じてさまざまな方法で列挙値を表示できます。  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## 参照  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)