---
title: 型&#39; &lt;typename&gt; &#39;が定義されていません
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 20f36a06000d0197ad80b83766f6612a474d5758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595187"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>型&#39; &lt;typename&gt; &#39;が定義されていません
ステートメントには、定義されていない型への参照が行われます。 などの宣言ステートメントで型を定義できます`Enum`、 `Structure`、 `Class`、または`Interface`です。  
  
 **エラー ID:** BC30002  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   型の定義とその参照の両方で同じスペル チェックを使用していることを確認します。  
  
-   型定義に、参照にアクセスできることを確認します。 たとえば、型が別のモジュールでは、宣言されている場合`Private`、参照元のモジュール、型定義を移動または宣言`Public`です。  
  
-   型の名前空間がプロジェクト内で再定義されていないことを確認します。 場合を使用して、`Global`キーワード、型名を完全に修飾します。 たとえば、プロジェクトにという名前空間が定義されている場合`System`、<xref:System.Object?displayProperty=nameWithType>で完全修飾されている場合を除き、型にアクセスできません、`Global`キーワード:`Global.System.Object`です。  
  
-   型が定義されている場合、オブジェクト ライブラリまたはタイプ ライブラリが定義されているが、Visual Basic、クリックで登録されていない場合**参照の追加**上、**プロジェクト**メニューのおよび適切なオブジェクトを選択ライブラリまたはタイプ ライブラリ。  
  
-   種類が対象となる .NET Framework プロファイルの一部であるアセンブリ内であることを確認します。 詳細については、「[.NET Framework を対象とするエラーのトラブルシューティング](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
