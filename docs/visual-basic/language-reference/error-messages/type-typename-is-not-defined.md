---
title: "型 &quot;&lt;typename&gt;&quot; が定義されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
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
ms.openlocfilehash: 09aa7c535fd5e17ddcd0e743fb5ec17ebadd4f7d
ms.lasthandoff: 03/13/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a>型 '&lt;typename&gt;' が定義されていません
ステートメントでは、定義されていない型への参照をしました。 などの宣言ステートメントで型を定義できる`Enum`、 `Structure`、 `Class`、または`Interface`です。  
  
 **エラー ID:** BC30002  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   型の定義とその参照の両方で同じスペル チェックを使用していることを確認します。  
  
-   型の定義が参照にアクセスできることを確認します。 たとえば、型が別のモジュールでは、宣言されている場合`Private`を参照しているモジュールに、型定義を移行または宣言`Public`します。  
  
-   型の名前空間がプロジェクト内で再定義されていないことを確認します。 使用している場合、`Global`完全型名を修飾するキーワードです。 たとえば、プロジェクトに名前空間が定義されている場合`System`、<xref:System.Object?displayProperty=fullName>で完全修飾されている場合を除き、型にアクセスできません、`Global`キーワード: `Global.System.Object`</xref:System.Object?displayProperty=fullName> 。  
  
-   型を定義するとしても、オブジェクト ライブラリまたはが定義されているタイプ ライブラリに登録されていない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、 をクリックして**参照の追加**上、**プロジェクト**] メニューの [し適切なオブジェクト ライブラリまたはタイプ ライブラリを選択します。  
  
-   対象となる .NET Framework プロファイルの一部であるアセンブリで型があることを確認します。 詳細については、次を参照してください。 [.NET Framework を対象とするエラーのトラブルシューティング](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [プロジェクト内の参照の管理](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)
