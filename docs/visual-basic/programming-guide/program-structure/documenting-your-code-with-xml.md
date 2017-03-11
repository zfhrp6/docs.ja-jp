---
title: "Documenting Your Code with XML (Visual Basic) | Microsoft Docs"
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
  - "XML, documenting code"
  - "XML comments, Visual Basic"
  - "Visual Basic code, documenting with XML"
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Documenting Your Code with XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、XML を使用して、コードのドキュメントを作成できます。  
  
## XML ドキュメントのコメント  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、プロジェクトの XML ドキュメントを簡単な方法で自動的に作成できます。  型およびメンバーの XML スケルトンを自動的に生成したうえで、概要、各パラメーターの説明ドキュメント、およびその他のコメントを指定できます。  適切なセットアップにより、XML ドキュメントは、プロジェクトと同じ名前に .xml という拡張子を付けた XML ファイルとして自動的に作成されます。  詳細については、「[\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。  
  
 この XML ファイルを利用したり、何らかの形で XML として操作することが可能です。  このファイルは、プロジェクトの出力ファイル \(.exe ファイルまたは .dll ファイル\) と同じディレクトリに配置されます。  
  
 XML ドキュメントの先頭は `'''` です。  コメントの処理には、次の制限があります。  
  
-   ドキュメントは、適切な XML であることが必要です。  XML が整形式でない場合、警告が生成され、エラーが発生したことを示すコメントがドキュメント ファイルに記述されます。  
  
-   開発者は、独自のタグ セットを自由に作成できます。  タグのセットには、推奨のものがあります \(このトピックの「関連項目」を参照してください\)。  推奨されるタグには、次のような特殊な意味を持つタグがあります。  
  
    -   \<param\> タグは、パラメーターの記述に使用します。  このタグを使用した場合、コンパイラはパラメーターが存在するかどうか、およびすべてのパラメーターがドキュメントに記述されているかどうかを検査します。  検査に失敗した場合、コンパイラは警告を発行します。  
  
    -   `cref` 属性をタグに追加すると、コード要素を参照できます。  コンパイラは、このコード要素が存在することを検査します。  検査に失敗した場合、コンパイラは警告を発行します。  また、コンパイラは、`cref` 属性で指定されている型を検索するときに、`Imports` ステートメントを考慮に入れます。  
  
    -   \<summary\> タグは、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で型またはメンバーについての追加的な情報を表示するために、IntelliSense によって使用されます。  
  
## 関連項目  
 ドキュメント コメントを記述した XML ファイルの作成の詳細については、以下のトピックを参照してください。  
  
-   [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Processing the XML File](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio の XML ツール](/visual-studio/xml-tools/xml-tools-in-visual-studio)  
  
## 参照  
 [Visual Basic でのアプリケーションの開発](../../../visual-basic/developing-apps/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)