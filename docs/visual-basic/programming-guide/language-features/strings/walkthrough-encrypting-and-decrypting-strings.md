---
title: Visual Basic における文字列の暗号化および暗号化
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651224"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>チュートリアル : Visual Basic での文字列の暗号化と複合化
このチュートリアルで使用する方法、<xref:System.Security.Cryptography.DESCryptoServiceProvider>クラスを暗号化および暗号化サービス プロバイダー (CSP) バージョンのトリプル データ暗号化標準を使用して文字列の暗号化を解除 (<xref:System.Security.Cryptography.TripleDES>) アルゴリズム。 最初の手順では、3 des アルゴリズムをカプセル化して、base 64 エンコード文字列として、暗号化されたデータを格納する単純なラッパー クラスを作成します。 その後、そのラッパーを使用して、パブリックにアクセスできるテキスト ファイルにプライベート ユーザー データを安全に保管します。  
  
 ユーザーの機密情報 (パスワードなど) を保護し、未承認ユーザーが資格情報を解読できないようにするには、暗号化を使用することができます。 これにより、ユーザーの資産を保護し、否認不可を提供する承認されたユーザーの id が盗まれないが保護することができます。 また、暗号化は、未承認ユーザーがアクセスできないユーザーのデータを保護できます。  
  
 詳細については、「[暗号サービス](../../../../standard/security/cryptographic-services.md)」をご覧ください。  
  
> [!IMPORTANT]
>  Rijndael (Advanced Encryption Standard [AES] と呼ばれるようになりました) および Triple Data Encryption Standard (3 des) アルゴリズム詳細いるため、DES よりも大きいセキュリティを実現負荷の大きい計算します。 詳細については、<xref:System.Security.Cryptography.DES> および <xref:System.Security.Cryptography.Rijndael> を参照してください。  
  
### <a name="to-create-the-encryption-wrapper"></a>暗号化のラッパーを作成するには  
  
1.  作成、`Simple3Des`暗号化と復号化メソッドをカプセル化するクラス。  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  含むファイルの先頭に暗号化の名前空間のインポートを追加、`Simple3Des`クラスです。  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  `Simple3Des`クラス、3 des 暗号化サービス プロバイダーを格納するためのプライベート フィールドを追加します。  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  指定したキーのハッシュから指定された長さのバイト配列を作成するプライベート メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  3 des 暗号化サービス プロバイダーの初期化にコンス トラクターを追加します。  
  
     `key`パラメーター コントロール、`EncryptData`と`DecryptData`メソッドです。  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  文字列を暗号化するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  文字列の暗号化を解除するパブリック メソッドを追加します。  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     ラッパー クラスは、ユーザーの資産を保護するようになりました使用できます。 この例では、パブリックにアクセスできるテキスト ファイルにプライベート ユーザー データを安全に保管することが使用されます。  
  
### <a name="to-test-the-encryption-wrapper"></a>暗号化のラッパーをテストするには  
  
1.  別のクラスで、ラッパーを使用するメソッドを追加`EncryptData`のマイ ドキュメント フォルダーの文字列を暗号化して、ユーザーに書き込む方法です。  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  ユーザーから、暗号化された文字列を読み取るメソッドがのマイ ドキュメント フォルダーと、ラッパーの文字列を復号化に追加`DecryptData`メソッドです。  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  呼び出すユーザー インターフェイスのコードを追加、`TestEncoding`と`TestDecoding`メソッドです。  
  
4.  アプリケーションを実行します。  
  
     アプリケーションをテストする場合は、こと、暗号化は解除されませんデータ、間違ったパスワードを指定する場合に注意してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [暗号サービス](../../../../standard/security/cryptographic-services.md)
