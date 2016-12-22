---
title: "Walkthrough: Encrypting and Decrypting Strings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "encryption, strings"
  - "strings [Visual Basic], encrypting"
  - "decryption, strings"
  - "strings [Visual Basic], decrypting"
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Encrypting and Decrypting Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このチュートリアルでは <xref:System.Security.Cryptography.DESCryptoServiceProvider> クラスを使用して、TDES \(Triple Data Encryption Standard\) アルゴリズム \(<xref:System.Security.Cryptography.TripleDES>\) の暗号化サービス プロバイダー \(CSP: Cryptographic Service Provider\) バージョンを用いた文字列の暗号化と復号化を行う方法について説明します。  最初に、3DES アルゴリズムをカプセル化し、暗号化されたデータを ベース 64 でエンコードされた文字列として格納する簡単なラッパー クラスを作成します。  次に、そのラッパーを使用して、プライベートなユーザー データをパブリックにアクセス可能なテキスト ファイルに安全に格納します。  
  
 暗号化を使用すると、ユーザーのシークレット \(たとえばパスワードなど\) を保護したり、未承認のユーザーによる資格情報の解読を不可能にしたりできます。  これにより、承認されたユーザーの ID が盗まれないように保護できるため、ユーザーの資産が保護されます。また、否認が不可能になります。  暗号化を行うと、ユーザー データが未承認のユーザーからアクセスされないように保護することも可能になります。  
  
 詳細については、「[暗号サービス](../Topic/Cryptographic%20Services.md)」を参照してください。  
  
> [!IMPORTANT]
>  Rijndael \(最近では AES \(Advanced Encryption Standard\) とも呼ばれる\) アルゴリズムや 3DES \(Triple Data Encryption Standard\) アルゴリズムは、暗号化のための計算量が非常に多いことから、DES よりもかなり高いセキュリティを実現します。  詳細については、「<xref:System.Security.Cryptography.DES>」および「<xref:System.Security.Cryptography.Rijndael>」を参照してください。  
  
### 暗号化のラッパーを作成するには  
  
1.  暗号化と復号化メソッドをカプセル化する `Simple3Des` のクラスを作成します。  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  `Simple3Des` のクラスを含むファイルの先頭に、暗号化の名前空間のインポートを追加します。  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  `Simple3Des` のクラスでは、3DES暗号化サービス プロバイダーを格納するためのプライベート フィールドを追加します。  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  指定されたキーのハッシュから指定された長さのバイト配列を作成するプライベート メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  3DES 暗号化サービス プロバイダーを初期化するためのコンストラクターを追加します。  
  
     `key` パラメーターは `EncryptData` メソッドと `DecryptData` メソッドを制御します。  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  文字列を暗号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  文字列を復号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     これで、ラッパークラスを使用してユーザーの資産を保護できるようになりました。  ラッパー クラスを使用して、プライベートなユーザー データをパブリックにアクセス可能なテキスト ファイルに安全に格納する例を次に示します。  
  
### 暗号化のラッパーをテストするには  
  
1.  別のクラスで、ラッパーの `EncryptData` メソッドを使用して文字列を暗号化し、それをユーザーのマイ ドキュメント フォルダーに書き込むメソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  暗号化された文字列を、ユーザーのマイ ドキュメント フォルダーから読み取り、その文字列をラッパーの `DecryptData` メソッドを使って復号化するメソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  `TestEncoding` メソッドと `TestDecoding` メソッドを呼び出すためのユーザー インターフェイス コードを追加します。  
  
4.  アプリケーションを実行します。  
  
     アプリケーションをテストするとき、間違ったパスワードを入力するとデータが復号化されないので注意してください。  
  
## 参照  
 <xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael>   
 [暗号サービス](../Topic/Cryptographic%20Services.md)