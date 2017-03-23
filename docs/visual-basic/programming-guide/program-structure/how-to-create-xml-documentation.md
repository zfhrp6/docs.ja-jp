---
title: "方法: Visual Basic での XML ドキュメントの作成 |Microsoft ドキュメント"
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 363a20c0fce05566b61e764d05932a9dfb779f90
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>方法 : Visual Basic で XML ドキュメントを作成する
この例では、XML ドキュメントのコメントをコードに追加する方法を示します。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>型またはメンバーの XML ドキュメントを作成するには  
  
1.  **コード エディター**ドキュメントを作成する型またはメンバー上の行にカーソルを移動します。  
  
2.  型`'''`(3 つの単一引用符付き)。  
  
     型またはメンバーの XML スケルトンが追加された、**コード エディター**します。  
  
3.  適切なタグの間のわかりやすい情報を追加します。  
  
    > [!NOTE]
    >  各行を始める必要があります、XML ドキュメントのブロック内で行を追加する場合は、`'''`です。  
  
4.  新しい XML ドキュメント コメントを含む、型またはメンバーを使用する追加のコードを追加します。  
  
     IntelliSense のテキストを表示する、\<概要 > 型またはメンバーのタグ。  
  
5.  ドキュメント コメントを含む XML ファイルを生成するコードをコンパイルします。 詳細については、次を参照してください。 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)します。  
  
## <a name="see-also"></a>関連項目  
 [XML を使用してコードを文書化します。](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
