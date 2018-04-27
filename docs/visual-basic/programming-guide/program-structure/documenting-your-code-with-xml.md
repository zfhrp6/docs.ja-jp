---
title: XML の使用によるコードのドキュメントの作成 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d132fa514008d072158a0e6bedaff511c55b18c0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML の使用によるコードのドキュメントの作成 (Visual Basic)
Visual basic では XML を使用してコードを文書化することができます。  
  
## <a name="xml-documentation-comments"></a>XML ドキュメントのコメント  
 Visual Basic では、プロジェクトの XML ドキュメントを自動的に作成する簡単な方法を提供します。 型とメンバーに対する XML スケルトンを自動的に生成し、パラメーターごとに、その他の注釈の概要、説明的なドキュメントを提供できます。 適切なセットアップでは、.xml 拡張子と、プロジェクトと同じ名前を持つ XML ファイルに XML ドキュメントが自動的に生成されます。 詳細については、「[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。  
  
 XML ファイルを消費または XML として操作することができます。 このファイルは、プロジェクトの出力の .exe または .dll ファイルと同じディレクトリにあります。  
  
 XML ドキュメントの先頭`'''`です。 これらのコメントの処理にはいくつか制限があります。  
  
-   ドキュメントは整形式の XML である必要があります。 場合は、XML の形式が正しくありません、警告が生成され、ドキュメント ファイルにエラーが発生したことを示すコメントが含まれています。  
  
-   開発者は、独自のタグ セットを自由に作成できます。 推奨されるタグ (このトピックの「関連項目」を参照してください) 設定があります。 推奨されるタグの一部には特別な意味があります。  
  
    -   \<param> タグは、パラメーターの記述に使われます。 このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。 検証に失敗した場合、コンパイラは警告を発行します。  
  
    -   `cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。 コンパイラでは、このコード要素が存在することを確認します。 検証に失敗した場合、コンパイラは警告を発行します。 コンパイラではいずれかのことも考慮`Imports`ステートメントで示される型を探すときに、`cref`属性。  
  
    -   \<概要 > タグを型またはメンバーに関する追加情報を表示する Visual Studio での IntelliSense によって使用されます。  
  
## <a name="related-sections"></a>関連項目  
 ドキュメント コメントで、XML ファイルを作成する方法の詳細については、次のトピックを参照してください。  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [XML ファイルの処理](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio の XML ツール](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic でのアプリケーションの開発](../../../visual-basic/developing-apps/index.md)  
 [Visual Basic プログラミング ガイド](../../../visual-basic/programming-guide/index.md)
