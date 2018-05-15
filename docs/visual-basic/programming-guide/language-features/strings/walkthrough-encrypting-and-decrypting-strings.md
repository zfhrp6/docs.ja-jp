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
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="b4e0f-102">チュートリアル : Visual Basic での文字列の暗号化と複合化</span><span class="sxs-lookup"><span data-stu-id="b4e0f-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="b4e0f-103">このチュートリアルで使用する方法、<xref:System.Security.Cryptography.DESCryptoServiceProvider>クラスを暗号化および暗号化サービス プロバイダー (CSP) バージョンのトリプル データ暗号化標準を使用して文字列の暗号化を解除 (<xref:System.Security.Cryptography.TripleDES>) アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="b4e0f-104">最初の手順では、3 des アルゴリズムをカプセル化して、base 64 エンコード文字列として、暗号化されたデータを格納する単純なラッパー クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="b4e0f-105">その後、そのラッパーを使用して、パブリックにアクセスできるテキスト ファイルにプライベート ユーザー データを安全に保管します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="b4e0f-106">ユーザーの機密情報 (パスワードなど) を保護し、未承認ユーザーが資格情報を解読できないようにするには、暗号化を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="b4e0f-107">これにより、ユーザーの資産を保護し、否認不可を提供する承認されたユーザーの id が盗まれないが保護することができます。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="b4e0f-108">また、暗号化は、未承認ユーザーがアクセスできないユーザーのデータを保護できます。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="b4e0f-109">詳細については、「[暗号サービス](../../../../standard/security/cryptographic-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4e0f-110">Rijndael (Advanced Encryption Standard [AES] と呼ばれるようになりました) および Triple Data Encryption Standard (3 des) アルゴリズム詳細いるため、DES よりも大きいセキュリティを実現負荷の大きい計算します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="b4e0f-111">詳細については、<xref:System.Security.Cryptography.DES> および <xref:System.Security.Cryptography.Rijndael> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="b4e0f-112">暗号化のラッパーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b4e0f-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="b4e0f-113">作成、`Simple3Des`暗号化と復号化メソッドをカプセル化するクラス。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  <span data-ttu-id="b4e0f-114">含むファイルの先頭に暗号化の名前空間のインポートを追加、`Simple3Des`クラスです。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  <span data-ttu-id="b4e0f-115">`Simple3Des`クラス、3 des 暗号化サービス プロバイダーを格納するためのプライベート フィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  <span data-ttu-id="b4e0f-116">指定したキーのハッシュから指定された長さのバイト配列を作成するプライベート メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  <span data-ttu-id="b4e0f-117">3 des 暗号化サービス プロバイダーの初期化にコンス トラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="b4e0f-118">`key`パラメーター コントロール、`EncryptData`と`DecryptData`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  <span data-ttu-id="b4e0f-119">文字列を暗号化するパブリック メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  <span data-ttu-id="b4e0f-120">文字列の暗号化を解除するパブリック メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     <span data-ttu-id="b4e0f-121">ラッパー クラスは、ユーザーの資産を保護するようになりました使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="b4e0f-122">この例では、パブリックにアクセスできるテキスト ファイルにプライベート ユーザー データを安全に保管することが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="b4e0f-123">暗号化のラッパーをテストするには</span><span class="sxs-lookup"><span data-stu-id="b4e0f-123">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="b4e0f-124">別のクラスで、ラッパーを使用するメソッドを追加`EncryptData`のマイ ドキュメント フォルダーの文字列を暗号化して、ユーザーに書き込む方法です。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  <span data-ttu-id="b4e0f-125">ユーザーから、暗号化された文字列を読み取るメソッドがのマイ ドキュメント フォルダーと、ラッパーの文字列を復号化に追加`DecryptData`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  <span data-ttu-id="b4e0f-126">呼び出すユーザー インターフェイスのコードを追加、`TestEncoding`と`TestDecoding`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="b4e0f-127">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-127">Run the application.</span></span>  
  
     <span data-ttu-id="b4e0f-128">アプリケーションをテストする場合は、こと、暗号化は解除されませんデータ、間違ったパスワードを指定する場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b4e0f-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e0f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4e0f-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [<span data-ttu-id="b4e0f-130">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="b4e0f-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
