---
title: "名前&lt;namespacename&gt;ルート名前空間に&lt;fullnamespacename&gt; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7342c7e85cce6c0e5892c4ad1826907dc03ed808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a>名前&lt;namespacename&gt;ルート名前空間に&lt;fullnamespacename&gt; CLS 準拠ではありません
アセンブリとしてマークされている`<CLSCompliant(True)>`、ルート名前空間の名前の要素がアンダー スコアで始まるが (`_`)。  
  
 プログラミング要素に準拠するためには、1 つまたは複数アンダー スコアを含めることができます、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) に始めることはできません、アンダー スコアを使用します。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40039  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠を必要とする場合は、ルート名前空間の名前を変更してから、その要素のいずれもがアンダー スコアで始まるようにします。  
  
-   名前空間の名前は変更されていないことを必要とする場合、削除、<xref:System.CLSCompliantAttribute>アセンブリからとしてマークまたは`<CLSCompliant(False)>`です。  
  
## <a name="see-also"></a>関連項目  
 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [\<経由で PAVE > CLS 準拠コードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
