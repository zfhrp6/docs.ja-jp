---
title: "XML (Visual Basic) を使用してコードを文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ec4907ff96a0861f97de21bdf45662c558d0a95
ms.lasthandoff: 03/13/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML の使用によるコードのドキュメントの作成 (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML を使用してコードを文書化することができます  
  
## <a name="xml-documentation-comments"></a>XML ドキュメントのコメント  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクトの XML ドキュメントを自動的に作成する簡単な方法を提供します。 型とメンバーの XML スケルトンを自動的に生成し、パラメーターごとに、その他の注釈の概要、説明的なドキュメントを提供できます。 適切なセットアップは、.xml 拡張子と、プロジェクトと同じ名前の XML ファイルに XML ドキュメントが自動的に生成されます。 詳細については、次を参照してください。 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)します。  
  
 XML ファイルを使用または XML として操作できます。 このファイルは、プロジェクトの出力 .exe または .dll ファイルと同じディレクトリにあります。  
  
 XML ドキュメントの先頭`'''`します。 これらのコメントの処理には、いくつかの制限があります。  
  
-   ドキュメントが整形式である XML です。 XML の形式が正しくない場合、は、警告が生成され、ドキュメント ファイルにエラーが発生したことを示すコメントが含まれています。  
  
-   開発者は、自由に独自のタグのセットを作成できます。 推奨されるタグ (このトピックの「関連項目」を参照してください) 設定があります。 推奨されるタグの一部は、特別な意味を持っています。  
  
    -   \<Param > タグを使用して、パラメーターを説明します。 使用する場合、コンパイラは、パラメーターが存在して、すべてのパラメーターが、ドキュメントに記載されているを確認します。 検証に失敗した場合、コンパイラは警告を発します。  
  
    -   `cref`属性は、コード要素への参照を提供する任意のタグに関連付けることができます。 コンパイラは、このコード要素が存在することを確認します。 検証に失敗した場合、コンパイラは警告を発します。 コンパイラではいずれかのことも考慮`Imports`ステートメントで示される型を探すときに、`cref`属性です。  
  
    -   \<概要 > タグを使用してでは、IntelliSense によって[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]型またはメンバーに関する追加情報を表示します。  
  
## <a name="related-sections"></a>関連項目  
 ドキュメントのコメントを XML ファイルの作成方法の詳細については、次のトピックを参照してください。  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [XML ファイルの処理](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio の XML ツール](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic でのアプリケーションの開発](../../../visual-basic/developing-apps/index.md)   
 [Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md)
