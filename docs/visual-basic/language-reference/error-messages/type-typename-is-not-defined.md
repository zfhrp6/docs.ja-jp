---
title: 型 &#39;&lt;typename&gt;&#39; が定義されていません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>型 &#39;&lt;typename&gt;&#39; が定義されていません
ステートメントには、定義されていない型への参照が行われます。 などの宣言ステートメントで型を定義できます`Enum`、 `Structure`、 `Class`、または`Interface`です。  
  
 **エラー ID:** BC30002  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   型の定義とその参照の両方で同じスペル チェックを使用していることを確認します。  
  
-   型定義に、参照にアクセスできることを確認します。 たとえば、型が別のモジュールでは、宣言されている場合`Private`、参照元のモジュール、型定義を移動または宣言`Public`です。  
  
-   型の名前空間がプロジェクト内で再定義されていないことを確認します。 場合を使用して、`Global`キーワード、型名を完全に修飾します。 たとえば、プロジェクトにという名前空間が定義されている場合`System`、<xref:System.Object?displayProperty=nameWithType>で完全修飾されている場合を除き、型にアクセスできません、`Global`キーワード:`Global.System.Object`です。  
  
-   型が定義されている場合、オブジェクト ライブラリまたはが定義されているタイプ ライブラリに登録されていない場合[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]をクリックして**参照の追加**上、**プロジェクト**メニューのおよび適切なオブジェクトを選択ライブラリまたはタイプ ライブラリ。  
  
-   種類が対象となる .NET Framework プロファイルの一部であるアセンブリ内であることを確認します。 詳細については、「[.NET Framework を対象とするエラーのトラブルシューティング](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
