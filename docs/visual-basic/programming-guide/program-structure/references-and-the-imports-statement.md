---
title: "References and the Imports Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assemblies [Visual Basic], namespaces"
  - "references, assembly"
  - "namespaces, assemblies"
  - "referencing assemblies"
  - "Imports statement, referencing assemblies"
  - "assemblies [Visual Basic], references"
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# References and the Imports Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロジェクトで外部オブジェクトを使用できるようにするには、**\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の参照では、アセンブリを指すことができます。アセンブリはタイプ ライブラリに似ていますが、タイプ ライブラリより多くの情報を含んでいます。  
  
## Imports ステートメント  
 アセンブリには名前空間があります。  アセンブリへの参照を追加するときに、モジュール内におけるそのアセンブリの名前空間の参照可能範囲を制御する `Imports` ステートメントをモジュールに追加することもできます。  `Imports` ステートメントを使用すると、スコープのコンテキストを利用できるようになるため、名前空間の一部だけを使って参照を一意にできます。  
  
 `Imports` ステートメントの構文は次のとおりです。  
  
 `Imports` \[         `|` `Aliasname` \=\] `Namespace`  
  
 `Aliasname` には、インポートした名前空間を参照するためにコード内で使用する短い名前を指定します。  `Namespace` には、プロジェクト参照、プロジェクト内の定義、または前の `Imports` ステートメントを通じて使用できる名前空間を指定します。  
  
 1 つのモジュールで使用できる `Imports` ステートメントの数に制限はありません。  `Imports` ステートメントは、`Option`ステートメントとその他のコードとの間に記述する必要があります \(`Option` ステートメントがある場合\)。  
  
> [!NOTE]
>  プロジェクト参照を `Imports` ステートメントや `Declare` ステートメントと混同しないようにしてください。  プロジェクト参照は、アセンブリ内のオブジェクトなど、外部オブジェクトを [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プロジェクトで使用できるようにします。  `Imports` ステートメントは、プロジェクト参照へのアクセスを簡単にするためのものであり、`Imports` ステートメントを使って外部オブジェクトにアクセスすることはできません。  `Declare` ステートメントは、ダイナミック リンク ライブラリ \(DLL\) の外部プロシージャへの参照を宣言するときに使用します。  
  
## Imports ステートメントでのエイリアスの使用  
 `Imports` ステートメントを使用すると、参照の完全限定名を明示的に入力する必要がなくなるため、クラスのメソッドへのアクセスが簡単になります。  エイリアスを使用すると、名前空間の一部に覚えやすい名前を割り当てることができます。  たとえば、1 つの文字列を複数の行に表示するキャリッジ リターンとライン フィードは、<xref:Microsoft.VisualBasic?displayProperty=fullName> 名前空間にある <xref:Microsoft.VisualBasic.ControlChars> モジュールの一部です。  この定数をエイリアスを使わずにプログラムで使用するには、次のコードを入力する必要があります。  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` ステートメントは、モジュールの `Option` ステートメントの次の行に記述する必要があります。  <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName> モジュールをインポートして、エイリアスを割り当てる例は、次のコード片のとおりです。  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 これ以降、この名前空間を参照する場合は、次のように入力するだけで済みます。  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 `Imports` ステートメントでエイリアス名を指定しなかった場合は、インポートした名前空間で定義されている要素を修飾子を付けずにモジュール内で使用できます。  エイリアス名を指定した場合は、その名前空間に含まれている名前の修飾子としてエイリアス名を使用する必要があります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic>   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法: コマンド ラインを使用してアセンブリを作成および使用する](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)