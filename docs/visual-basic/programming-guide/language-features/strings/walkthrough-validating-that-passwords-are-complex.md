---
title: パスワードの複雑さ (Visual Basic) を検証します。
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: acfc8ab958c8671ed7f1afd245d24a43ca12be29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650284"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>チュートリアル: パスワードの複雑さの検証 (Visual Basic)
このメソッドは、強力なパスワードのいくつかの特性を確認しが失敗したパスワードをチェックに関する情報を含む文字列パラメーターを更新します。  
  
 パスワードは、ユーザーを承認するセキュリティで保護されたシステムで使用できます。 ただし、パスワードは、承認されていないが困難になると推測する必要があります。 攻撃者が使用できる、*辞書攻撃*プログラムでは、すべてのディクショナリ (または別の言語で複数の辞書) に単語を反復処理し、単語のすべてのユーザーのパスワードとして作業するかどうかをテストします。 「ヤンキース」または「ムスタング」などの脆弱なパスワードを簡単に推測できることができます。 強力なパスワードは、たとえば"しますか?'L1N3vaFiNdMeyeP@sSWerd!"に推測できる可能性が大幅に低下します。 パスワードで保護されたシステムには、強力なパスワードを選択することを確認します。  
  
 強力なパスワードは (大文字、小文字、数字、および特殊文字の組み合わせを含む) が複雑であり、word ではありません。 この例では、複雑さを検証する方法を示します。  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 パスワードを格納する文字列を渡すことによって、このメソッドを呼び出します。  
  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System.Text.RegularExpressions> 名前空間のメンバーへのアクセス許可。 コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
 パスワードをネットワーク経由で移動する場合は、データを転送するため、セキュリティで保護されたメソッドを使用する必要があります。 詳細については、次を参照してください。 [ASP.NET Web アプリケーションのセキュリティ](https://msdn.microsoft.com/library/330a99hc)です。  
  
 精度を向上させることができます、`ValidatePassword`の他の複雑性チェックを追加することによって機能します。  
  
-   パスワードとユーザーの名前、ユーザー識別子、およびアプリケーション定義の辞書に対してその部分文字列を比較します。 さらに、比較を実行するときに、同等と視覚的に類似する文字を処理します。 たとえば、「1」と「3」の数字と同等として文字"l"と"e"を扱います。  
  
-   1 つだけ大文字の文字がある場合、パスワードの最初の文字ではないことを確認します。  
  
-   パスワードの最後の 2 つの文字が文字であることを確認してください。  
  
-   すべてのシンボルがキーボードの一番上の行から入力したパスワードは許可されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Text.RegularExpressions.Regex>  
 [ASP.NET Web アプリケーションのセキュリティ](https://msdn.microsoft.com/library/330a99hc)
