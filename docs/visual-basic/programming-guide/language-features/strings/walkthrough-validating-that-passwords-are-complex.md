---
title: "パスワードの複雑さ (Visual Basic) の検証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
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
ms.openlocfilehash: e899900d60bddb83fb640abcc7f11f333c1af870
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>チュートリアル: パスワードの複雑さの検証 (Visual Basic)
このメソッドは、いくつかの強力なパスワードの特性をチェックし、失敗したパスワードをチェックに関する情報を文字列パラメーターを更新します。  
  
 パスワードは、ユーザーを承認するセキュリティで保護されたシステムで使用できます。 ただし、パスワードは、承認されていないユーザーを推測することが困難である必要があります。 攻撃者は、使用、*辞書攻撃*プログラムでは、辞書 (または別の言語で複数の辞書) 内の単語のすべてを反復処理し、ユーザーのパスワードとして作業、単語のいずれかどうかをテストします。 「ヤンキース」や「ムスタング」などの脆弱なパスワードを簡単に推測できることができます。 強力なパスワードなど、"でしょうか。'L1N3vaFiNdMeyeP@sSWerd!"に推測できる可能性が大幅に低下します。 パスワードで保護されたシステムでは、強力なパスワードを選択することを確認する必要があります。  
  
 強力なパスワードは、(大文字、小文字、数字、および特殊文字の組み合わせを含む) 複合語ではないです。 この例では、複雑さを検証する方法を示します。  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnRegEx&#1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このメソッドを呼び出すには、パスワードを格納する文字列を渡します。  
  
 この例で必要な要素は次のとおりです。  
  
-   メンバーへのアクセス、<xref:System.Text.RegularExpressions>名前空間</xref:System.Text.RegularExpressions>。 追加、`Imports`ステートメント、コード内のメンバー名を完全に修飾していない場合。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
 ネットワーク経由でパスワードを移動する場合は、データを転送するため、安全な方法を使用する必要があります。 詳細については、次を参照してください。 [ASP.NET Web アプリケーション セキュリティ](https://msdn.microsoft.com/library/330a99hc)します。  
  
 精度を向上させることができます、`ValidatePassword`の他の複雑性チェックを追加することによって機能します。  
  
-   パスワードとユーザーの名前、ユーザー id、およびアプリケーション定義の辞書からその部分文字列を比較します。 さらに、比較を実行するときに、同等であるという視覚的に類似する文字を扱います。 たとえば、「1」と「3」の数字と同等として文字"l"と"e"を扱います。  
  
-   大文字の&1; つだけの場合、パスワードの最初の文字ではないことを確認します。  
  
-   パスワードの最後の&2; つの文字がアルファベットの文字であることを確認してください。  
  
-   キーボードの一番上の行からのすべてのシンボルが入力したパスワードは許可されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex>   
 [ASP.NET Web アプリケーションのセキュリティ](https://msdn.microsoft.com/library/330a99hc)
