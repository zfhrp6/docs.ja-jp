---
title: 序数が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593604"
---
# <a name="ordinal-is-not-valid"></a>序数が有効ではありません。
プロシージャ名の代わりに、番号を使用してに示されているダイナミック リンク ライブラリ (DLL) への呼び出しを使用して、`#num`構文です。 このエラーには、次の考えられる原因があります。  
  
-   変換する、`#num`失敗序数する式。  
  
-   `#num`指定された DLL で任意の関数が指定されていません。  
  
-   タイプ ライブラリには、無効な序数の内部で使用されて結果として無効な宣言があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  名前でプロシージャを呼び出すまたは式が有効な数値を表すかどうかを確認します。  
  
2.  確認`#num`DLL 内の有効な関数を識別します。  
  
3.  問題の原因で、コードをコメント アウト、プロシージャ呼び出しを分離します。 書き込み、`Declare`プロシージャ、およびレポート、タイプ ライブラリのベンダーに、問題ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
