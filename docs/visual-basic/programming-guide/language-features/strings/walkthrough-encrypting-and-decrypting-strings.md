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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 460b0e6e84f5be23f0c811e48daf36d3d4af3d23
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="097df-102">チュートリアル : Visual Basic での文字列の暗号化と複合化</span><span class="sxs-lookup"><span data-stu-id="097df-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="097df-103">このチュートリアルで使用する方法、 <xref:System.Security.Cryptography.DESCryptoServiceProvider>Triple Data Encryption Standard の暗号化サービス プロバイダー (CSP) のバージョンを使用して文字列を暗号化/暗号化解除するクラス (<xref:System.Security.Cryptography.TripleDES>) アルゴリズム</xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.DESCryptoServiceProvider>。</span><span class="sxs-lookup"><span data-stu-id="097df-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="097df-104">最初の手順では、3 des アルゴリズムをカプセル化して、base64 でエンコードされた文字列として、暗号化されたデータを格納する単純なラッパー クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="097df-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="097df-105">次に、そのラッパーを使用して、安全にパブリックにアクセスできるテキスト ファイルにユーザーの個人データを格納します。</span><span class="sxs-lookup"><span data-stu-id="097df-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="097df-106">暗号化を使用するには、ユーザーの秘密情報 (パスワードなど) を保護し、承認されていないユーザーの資格情報を解読できないようにします。</span><span class="sxs-lookup"><span data-stu-id="097df-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="097df-107">これにより、ユーザーのアセットを保護し、否認不可を提供する承認されたユーザーの id が盗まれないが保護することができます。</span><span class="sxs-lookup"><span data-stu-id="097df-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="097df-108">また、暗号化は、承認されていないユーザーへのアクセスをユーザーのデータを保護できます。</span><span class="sxs-lookup"><span data-stu-id="097df-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="097df-109">詳細については、次を参照してください。 [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)します。</span><span class="sxs-lookup"><span data-stu-id="097df-109">For more information, see [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="097df-110">Rijndael (高度暗号化標準 [AES] と呼ばれるをするようになりました) と Triple Data Encryption Standard (3 des) アルゴリズム詳細、DES よりも優れたセキュリティを提供負荷の大きい計算します。</span><span class="sxs-lookup"><span data-stu-id="097df-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="097df-111">詳細については、「 <xref:System.Security.Cryptography.DES> <xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.DES>の使用」を参照していますください。</span><span class="sxs-lookup"><span data-stu-id="097df-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="097df-112">暗号化ラッパーを作成するには</span><span class="sxs-lookup"><span data-stu-id="097df-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="097df-113">作成、`Simple3Des`暗号化と復号化メソッドをカプセル化するクラス。</span><span class="sxs-lookup"><span data-stu-id="097df-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     <span data-ttu-id="097df-114">[!code-vb[VbVbalrStrings #&38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-114">[!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span></span>  
  
2.  <span data-ttu-id="097df-115">含むファイルの先頭に暗号化の名前空間のインポートを追加、`Simple3Des`クラスです。</span><span class="sxs-lookup"><span data-stu-id="097df-115">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     <span data-ttu-id="097df-116">[!code-vb[VbVbalrStrings #&77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-116">[!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span></span>  
  
3.  <span data-ttu-id="097df-117">`Simple3Des`クラスに 3 des 暗号化サービス プロバイダーを格納するプライベート フィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="097df-117">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="097df-118">[!code-vb[VbVbalrStrings&#39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-118">[!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span></span>  
  
4.  <span data-ttu-id="097df-119">指定したキーのハッシュから指定された長さのバイト配列を作成するプライベート メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="097df-119">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     <span data-ttu-id="097df-120">[!code-vb[VbVbalrStrings #&41;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-120">[!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span></span>  
  
5.  <span data-ttu-id="097df-121">3 des 暗号化サービス プロバイダーを初期化するコンス トラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="097df-121">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="097df-122">`key`パラメーター コントロール、`EncryptData`と`DecryptData`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="097df-122">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     <span data-ttu-id="097df-123">[!code-vb[VbVbalrStrings #&40;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-123">[!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span></span>  
  
6.  <span data-ttu-id="097df-124">文字列を暗号化するパブリック メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="097df-124">Add a public method that encrypts a string.</span></span>  
  
     <span data-ttu-id="097df-125">[!code-vb[VbVbalrStrings #&42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-125">[!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span></span>  
  
7.  <span data-ttu-id="097df-126">文字列を復号化するパブリック メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="097df-126">Add a public method that decrypts a string.</span></span>  
  
     <span data-ttu-id="097df-127">[!code-vb[VbVbalrStrings #&43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-127">[!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span></span>  
  
     <span data-ttu-id="097df-128">ラッパー クラスは、ユーザーの資産を保護するようになりました使用できます。</span><span class="sxs-lookup"><span data-stu-id="097df-128">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="097df-129">この例では安全にパブリックにアクセスできるテキスト ファイルにユーザーの個人データを格納に使用されます。</span><span class="sxs-lookup"><span data-stu-id="097df-129">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="097df-130">暗号化のラッパーをテストするには</span><span class="sxs-lookup"><span data-stu-id="097df-130">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="097df-131">別のクラスで、ラッパーを使用するメソッドを追加`EncryptData`のマイ ドキュメント フォルダーの文字列を暗号化し、それをユーザーに出力する方法です。</span><span class="sxs-lookup"><span data-stu-id="097df-131">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     <span data-ttu-id="097df-132">[!code-vb[VbVbalrStrings #&78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-132">[!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span></span>  
  
2.  <span data-ttu-id="097df-133">ユーザーから、暗号化された文字列を読み取るメソッドがのマイ ドキュメント フォルダーと、ラッパーの文字列を復号化追加`DecryptData`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="097df-133">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     <span data-ttu-id="097df-134">[!code-vb[VbVbalrStrings #&79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="097df-134">[!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span></span>  
  
3.  <span data-ttu-id="097df-135">呼び出すユーザー インターフェイスのコードを追加、`TestEncoding`と`TestDecoding`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="097df-135">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="097df-136">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="097df-136">Run the application.</span></span>  
  
     <span data-ttu-id="097df-137">アプリケーションをテストする場合は、こと、暗号化は解除されませんデータ間違ったパスワードを提供する場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="097df-137">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097df-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="097df-138">See Also</span></span>  
 <span data-ttu-id="097df-139"><xref:System.Security.Cryptography></xref:System.Security.Cryptography></span><span class="sxs-lookup"><span data-stu-id="097df-139"><xref:System.Security.Cryptography></span></span>   
 <span data-ttu-id="097df-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="097df-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></span></span>   
 <span data-ttu-id="097df-141"><xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="097df-141"><xref:System.Security.Cryptography.DES></span></span>   
 <span data-ttu-id="097df-142"><xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES></span><span class="sxs-lookup"><span data-stu-id="097df-142"><xref:System.Security.Cryptography.TripleDES></span></span>   
 <span data-ttu-id="097df-143"><xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael></span><span class="sxs-lookup"><span data-stu-id="097df-143"><xref:System.Security.Cryptography.Rijndael></span></span>   
<span data-ttu-id="097df-144"> [暗号サービス](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span><span class="sxs-lookup"><span data-stu-id="097df-144"> [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span></span>
