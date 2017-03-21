---
title: "Visual Basic における文字列の暗号化および暗号化 |Microsoft ドキュメント"
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
- encryption, strings
- strings [Visual Basic], encrypting
- decryption, strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: ae3d599f7173162c07fbaeda60435615f101b10d
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>チュートリアル : Visual Basic での文字列の暗号化と複合化
このチュートリアルで使用する方法、 <xref:System.Security.Cryptography.DESCryptoServiceProvider>Triple Data Encryption Standard の暗号化サービス プロバイダー (CSP) のバージョンを使用して文字列を暗号化/暗号化解除するクラス (<xref:System.Security.Cryptography.TripleDES>) アルゴリズム</xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.DESCryptoServiceProvider>。 最初の手順では、3 des アルゴリズムをカプセル化して、base64 でエンコードされた文字列として、暗号化されたデータを格納する単純なラッパー クラスを作成します。 次に、そのラッパーを使用して、安全にパブリックにアクセスできるテキスト ファイルにユーザーの個人データを格納します。  
  
 暗号化を使用するには、ユーザーの秘密情報 (パスワードなど) を保護し、承認されていないユーザーの資格情報を解読できないようにします。 これにより、ユーザーのアセットを保護し、否認不可を提供する承認されたユーザーの id が盗まれないが保護することができます。 また、暗号化は、承認されていないユーザーへのアクセスをユーザーのデータを保護できます。  
  
 詳細については、次を参照してください。 [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)します。  
  
> [!IMPORTANT]
>  Rijndael (高度暗号化標準 [AES] と呼ばれるをするようになりました) と Triple Data Encryption Standard (3 des) アルゴリズム詳細、DES よりも優れたセキュリティを提供負荷の大きい計算します。 詳細については、「 <xref:System.Security.Cryptography.DES> <xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.DES>の使用」を参照していますください。  
  
### <a name="to-create-the-encryption-wrapper"></a>暗号化ラッパーを作成するには  
  
1.  作成、`Simple3Des`暗号化と復号化メソッドをカプセル化するクラス。  
  
     [!code-vb[VbVbalrStrings #&38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  含むファイルの先頭に暗号化の名前空間のインポートを追加、`Simple3Des`クラスです。  
  
     [!code-vb[VbVbalrStrings #&77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  `Simple3Des`クラスに 3 des 暗号化サービス プロバイダーを格納するプライベート フィールドを追加します。  
  
     [!code-vb[VbVbalrStrings&#39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  指定したキーのハッシュから指定された長さのバイト配列を作成するプライベート メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings #&41;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  3 des 暗号化サービス プロバイダーを初期化するコンス トラクターを追加します。  
  
     `key`パラメーター コントロール、`EncryptData`と`DecryptData`メソッドです。  
  
     [!code-vb[VbVbalrStrings #&40;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  文字列を暗号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings #&42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  文字列を復号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings #&43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     ラッパー クラスは、ユーザーの資産を保護するようになりました使用できます。 この例では安全にパブリックにアクセスできるテキスト ファイルにユーザーの個人データを格納に使用されます。  
  
### <a name="to-test-the-encryption-wrapper"></a>暗号化のラッパーをテストするには  
  
1.  別のクラスで、ラッパーを使用するメソッドを追加`EncryptData`のマイ ドキュメント フォルダーの文字列を暗号化し、それをユーザーに出力する方法です。  
  
     [!code-vb[VbVbalrStrings #&78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  ユーザーから、暗号化された文字列を読み取るメソッドがのマイ ドキュメント フォルダーと、ラッパーの文字列を復号化追加`DecryptData`メソッドです。  
  
     [!code-vb[VbVbalrStrings #&79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  呼び出すユーザー インターフェイスのコードを追加、`TestEncoding`と`TestDecoding`メソッドです。  
  
4.  アプリケーションを実行します。  
  
     アプリケーションをテストする場合は、こと、暗号化は解除されませんデータ間違ったパスワードを提供する場合に注意してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.Cryptography></xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael>   
 [暗号サービス](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)
