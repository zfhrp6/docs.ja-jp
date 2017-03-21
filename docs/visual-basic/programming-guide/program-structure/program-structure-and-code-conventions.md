---
title: "プログラム構造とコード規則 (Visual Basic) |Microsoft ドキュメント"
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
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cd25d99d74bf1e4d416c9da63758f6ad04027258
ms.lasthandoff: 03/13/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a>プログラム構造とコード規則 (Visual Basic)
ここでは、一般的な [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムの構造を紹介します。また、単純な [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラム "Hello World" を示し、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のコード規則について説明します。 コード規則は、プログラムのロジックではなくプログラムの物理的な構造と外観に焦点を合わせた提案です。 コード規則に従うと、コードの読み取り、理解、保守が簡単になります。 コード規則には、以下の内容が含まれます。  
  
-   コードのラベル付けとコメント付けに関する標準化された書式  
  
-   コードのスペーシング、書式指定、およびインデント設定に関するガイドライン  
  
-   オブジェクト、変数、およびプロシージャの名前付け規則  
  
 以下のトピックでは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムの一連のプログラミング ガイドラインを適切な使用例と共に示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Basic プログラムの構造](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムを構成する要素の概要を示します。  
  
 [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 アプリケーションの開始点となり、アプリケーションの総合的な制御を行うプロシージャについて説明します。  
  
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 他のアセンブリのオブジェクトを参照する方法を説明します。  
  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 アセンブリ内のオブジェクトが名前空間でどのように編成されているのかを説明します。  
  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 プロシージャ、定数、変数、引数、およびオブジェクトの名前付けに関する一般的なガイドラインを示します。  
  
 [Visual Basic のコーディング規則](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 このドキュメントのサンプルを開発するときに使用したガイドラインについてレビューします。  
  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 特定のコード ブロックを選択的にコンパイルし、その間は他のコード ブロックを無視する方法について説明します。  
  
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 長いステートメントを複数の行に分割する方法と、複数の短いステートメントを&1; 行に結合する方法を示します。  
  
 [方法 : コードのセクションを折りたたんで非表示にする](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のコード エディターでコードをセクションごとに折りたたんで非表示にする方法について説明します。  
  
 [方法 : ステートメントへのラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 `On Error Goto` などのステートメントで使用するために、コード行に識別用のマーキングをする方法について説明します。  
  
 [コード内の特殊文字](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 英数字以外の文字を使用する方法と場所について説明します。  
  
 [コード内のコメント](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 説明的なコメントをコードに追加する方法について説明します。  
  
 [コード内の要素名としてのキーワード](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 角かっこ (`[]`) を使用して [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] キーワードにもなる変数名を区切る方法について説明します。  
  
 [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムの要素を参照するさまざまな方法について説明します。  
  
 [Visual Basic の制限事項](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の既知のコーディングの制限の解除について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [表記規則とコード規則](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の標準的なコーディング規則について説明します。  
  
 [コードの作成](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 コードの記述と管理を容易にする機能について説明します。
