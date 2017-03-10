---
title: "Processing the XML File (Visual Basic) | Microsoft Docs"
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
  - "XML comments, parsing [Visual Basic]"
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Processing the XML File (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラは、ドキュメントを生成するためにタグ付けされたコードの構成体ごとに、ID 文字列を生成します。  \(コードにタグを付ける方法については、「[XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)」を参照してください\)。ID 文字列によって、構成体は一意に識別されます。  XML ファイルを処理するプログラムは、ID 文字列を使用して、対応する [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] メタデータ\/リフレクション項目を識別できます。  
  
 XML ファイルは、コードの階層的表現ではなく、要素ごとに生成された ID のあるフラットなリストです。  
  
 コンパイラは、次の規則に基づいて ID 文字列を生成します。  
  
-   生成される文字列に空白は含まれません。  
  
-   ID 文字列の最初の部分には、単一の文字とコロンで、識別されるメンバーの種類を示します。  使用されるメンバー型は次のとおりです。  
  
|||  
|-|-|  
|文字|Description|  
|N|namespace<br /><br /> 名前空間にはドキュメント コメントを追加できませんが、サポートされている場合は、ドキュメント コメントへの CREF 参照を作成できます。|  
|T|型: `Class`、`Module`、`Interface`、`Structure`、`Enum`、`Delegate`。|  
|F|フィールド: `Dim`。|  
|P|プロパティ: `Property` \(既定のプロパティを含む\)。|  
|M|メソッド: `Sub`、`Function`、`Declare`、`Operator`。|  
|E|イベント: `Event`。|  
|\!|エラー文字列<br /><br /> エラーに続く文字列で、エラーの内容を示します。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、解決できないリンクのエラー情報を生成します。|  
  
-   `String` の 2 番目の部分は、項目の完全修飾名です。名前は、名前空間のルートから始まります。  項目の名前、項目が含まれている型、および名前空間は、ピリオド \(.\) で区切られます。  項目の名前自体にピリオドが含まれている場合は、シャープ記号 \(\#\) に置き換えられます。  項目の名前にはシャープ記号がないことが前提です。  たとえば、`String` コンストラクターの完全修飾名は `System.String.#ctor` となります。  
  
-   プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。  引数がない場合は、かっこはありません。  引数の区切り文字には、コンマを使用します。  各引数は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のシグネチャでの引数のエンコードとまったく同じ方法でエンコードされます。  
  
## 使用例  
 次のコードは、クラスおよびそのメンバーの ID 文字列がどのように生成されるかを示します。  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/processing-the-xml-file_1.vb)]  
  
## 参照  
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)