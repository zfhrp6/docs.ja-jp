---
title: "How to: Create XML Documentation in Visual Basic | Microsoft Docs"
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
  - "XML comments"
  - "XML documentation, creating"
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Create XML Documentation in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

この例は、XML ドキュメントのコメントをコードに追加する方法を示しています。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 型またはメンバーに対して XML ドキュメントを作成するには  
  
1.  **コード エディター**で、ドキュメントを作成する対象の型またはメンバーの上の行にカーソルを置きます。  
  
2.  `'''` \(3 つの単一引用符\) を入力します。  
  
     型またはメンバーに対する XML スケルトンが**コード エディター**に追加されます。  
  
3.  適切なタグの間に説明情報を追加します。  
  
    > [!NOTE]
    >  XML ドキュメント ブロック内に行を追加した場合、各行の先頭は `'''` である必要があります。  
  
4.  XML ドキュメントの新しいコメントを指定した型またはメンバーを使用するコードを追加します。  
  
     IntelliSense により、当該の型またはメンバーに対する \<summary\> タグのテキストが表示されます。  
  
5.  コードをコンパイルし、ドキュメントのコメントを含む XML ファイルを生成します。  詳細については、「[\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。  
  
## 参照  
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)