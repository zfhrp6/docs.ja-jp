---
title: "方法 : Visual Basic で XML ドキュメントを作成する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>方法 : Visual Basic で XML ドキュメントを作成する
この例では、XML ドキュメント コメントをコードに追加する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>型またはメンバーの XML ドキュメントを作成するには  
  
1.  **コード エディター**ドキュメントを作成する型またはメンバー上の行にカーソルを移動します。  
  
2.  型`'''`(3 つ単一引用符)。  
  
     XML スケルトンの型またはメンバーを追加、**コード エディター**です。  
  
3.  適切なタグの間で情報を追加します。  
  
    > [!NOTE]
    >  それぞれの線が始まる必要があります、XML ドキュメントのブロック内で行を追加する場合`'''`です。  
  
4.  新しい XML ドキュメントのコメントに型またはメンバーを使用する追加のコードを追加します。  
  
     IntelliSense のテキストを表示する、\<概要 > 型またはメンバーのタグ。  
  
5.  ドキュメント コメントを含む XML ファイルを生成するコードをコンパイルします。 詳細については、「[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
