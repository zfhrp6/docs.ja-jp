---
title: "Walkthrough: Validating That Passwords Are Complex (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "String data type, validation"
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Walkthrough: Validating That Passwords Are Complex (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、強力なパスワードの特性をチェックし、パスワードの複雑さのチェックに関する情報を使って文字列パラメーターを更新するための方法について説明します。  
  
 パスワードは、セキュリティ保護されたシステムでユーザーを承認するために使用します。  しかし、パスワードは許可されないユーザーから簡単に推測されないために、複雑であることが必要です。  攻撃者は、ある辞書内 \(または、さまざな言語の複数の辞書内\) のすべての語を反復処理して、その中にユーザーのパスワードと一致するものがあるかどうかを調べる*辞書攻撃*プログラムを使用する場合があります。  "Yankees" や "Mustang" などの脆弱なパスワードでは、簡単に推測される可能性があります。  "?You'L1N3vaFiNdMeyeP@sSWerd\!" などのより強力なパスワードであれば、推測される可能性はかなり低くなります。  システムをパスワードで保護する場合は、ユーザーが強力なパスワードを選択していることを確認する必要があります。  
  
 強力なパスワードとは、複雑 \(大文字と小文字、数字、および特殊文字を組み合わせていること\) で、単語ではないパスワードです。  次の例は、複雑さを検査する方法を示しています。  
  
## 例  
  
### コード  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## コードのコンパイル  
 このメソッドを呼び出すには、パスワードを格納する文字列を渡します。  
  
 この例には、次の項目が必要です。  
  
-   <xref:System.Text.RegularExpressions> 名前空間のメンバーに対するアクセス。  コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。  詳細については、「[Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## セキュリティ  
 ネットワーク経由でパスワードを渡す場合は、安全な方法を使用してデータを転送する必要があります。  詳細については、「[ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md)」を参照してください。  
  
 次に示す方法で複雑さのチェックを追加すると、`ValidatePassword` 関数の精度を高めることができます。  
  
-   パスワードとその部分文字列を、ユーザー名、ユーザー ID、およびアプリケーション定義の辞書と比較します。  また、比較を実行するときには、外見が似ている文字を同等として扱ってください。  たとえば、"l" と "e" の文字は、"1" と "3" の数字と同等として扱います。  
  
-   大文字を 1 つしか使っていない場合は、それがパスワードの先頭の文字でないことを確認します。  
  
-   パスワードの最後の 2 文字がアルファベット文字であることを確認します。  
  
-   すべての記号がキーワードの一番上の行から入力されているパスワードを禁止します。  
  
## 参照  
 <xref:System.Text.RegularExpressions.Regex>   
 [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md)