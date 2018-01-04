---
title: "方法 : ハードウェア暗号化デバイスにアクセスする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9670c4a205e7700289a2e0d955e264c50a0e341
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="21268-102">方法 : ハードウェア暗号化デバイスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="21268-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="21268-103">ハードウェア暗号化デバイスにアクセスするには、<xref:System.Security.Cryptography.CspParameters> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="21268-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="21268-104">たとえば、このクラスを使用すると、アプリケーションをスマート カード、ハードウェアの乱数ジェネレーター、または特定の暗号化アルゴリズムのハードウェア実装と統合することができます。</span><span class="sxs-lookup"><span data-stu-id="21268-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="21268-105"><xref:System.Security.Cryptography.CspParameters> クラスは、正しくインストールされたハードウェア暗号化デバイスにアクセスする暗号化サービス プロバイダー (CSP) を作成します。</span><span class="sxs-lookup"><span data-stu-id="21268-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="21268-106">レジストリ エディター (Regedit.exe)  を使用してレジストリ キー (HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider) を調べることで、CSP を使用できるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="21268-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="21268-107">キー カードを使用してデータに署名するには</span><span class="sxs-lookup"><span data-stu-id="21268-107">To sign data using a key card</span></span>  
  
1.  <span data-ttu-id="21268-108">整数のプロバイダー型とプロバイダーの名前をコンストラクターに渡す、<xref:System.Security.Cryptography.CspParameters> クラスのインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="21268-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2.  <span data-ttu-id="21268-109">新規作成された <xref:System.Security.Cryptography.CspParameters> オブジェクトの <xref:System.Security.Cryptography.CspParameters.Flags%2A> プロパティに適切なフラグを渡します。</span><span class="sxs-lookup"><span data-stu-id="21268-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="21268-110">たとえば、<xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> フラグを渡します。</span><span class="sxs-lookup"><span data-stu-id="21268-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3.  <span data-ttu-id="21268-111"><xref:System.Security.Cryptography.CspParameters> オブジェクトをコンストラクターに渡す、<xref:System.Security.Cryptography.AsymmetricAlgorithm> クラス (<xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスなど) のインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="21268-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4.  <span data-ttu-id="21268-112">`Sign` メソッドのいずれかを使用してデータに署名し、`Verify` メソッドのいずれかを使用してデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="21268-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="21268-113">ハードウェアの乱数ジェネレーターを使用して乱数を生成するには</span><span class="sxs-lookup"><span data-stu-id="21268-113">To generate a random number using a hardware random number generator</span></span>  
  
1.  <span data-ttu-id="21268-114">整数のプロバイダー型とプロバイダーの名前をコンストラクターに渡す、<xref:System.Security.Cryptography.CspParameters> クラスのインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="21268-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2.  <span data-ttu-id="21268-115"><xref:System.Security.Cryptography.CspParameters> オブジェクトをコンストラクターに渡す、<xref:System.Security.Cryptography.RNGCryptoServiceProvider> のインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="21268-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3.  <span data-ttu-id="21268-116"><xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> メソッドまたは <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> メソッドを使用してランダムな値を作成します。</span><span class="sxs-lookup"><span data-stu-id="21268-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21268-117">例</span><span class="sxs-lookup"><span data-stu-id="21268-117">Example</span></span>  
 <span data-ttu-id="21268-118">次のコード例は、スマート カードを使用してデータに署名する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="21268-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="21268-119">このコード例は、スマート カードを公開する <xref:System.Security.Cryptography.CspParameters> オブジェクトを作成してから、CSP を使用して <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="21268-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="21268-120">コード例では、続いて幾らかのデータの署名と確認を行います。</span><span class="sxs-lookup"><span data-stu-id="21268-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="21268-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="21268-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="21268-122"><xref:System> 名前空間と <xref:System.Security.Cryptography> 名前空間を含めます。</span><span class="sxs-lookup"><span data-stu-id="21268-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
-   <span data-ttu-id="21268-123">スマート カード リーダーとドライバーをコンピューターにインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="21268-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
-   <span data-ttu-id="21268-124">カード リーダー固有の情報を使用して、<xref:System.Security.Cryptography.CspParameters> オブジェクトを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21268-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="21268-125">詳細については、カード リーダーのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="21268-125">For more information, see the documentation of your card reader.</span></span>
