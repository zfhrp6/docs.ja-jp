---
title: ハッシュ コードによるデータの整合性の保証
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27e4abcd5e8dfe253ba8a7ea1ba5022561ed9ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581574"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="8abb7-102">ハッシュ コードによるデータの整合性の保証</span><span class="sxs-lookup"><span data-stu-id="8abb7-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="8abb7-103">ハッシュ値は、データを一意に識別する固定長の数値です。</span><span class="sxs-lookup"><span data-stu-id="8abb7-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="8abb7-104">ハッシュ値は、大量のデータを非常に小さな数値として表現するため、デジタル署名と一緒に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="8abb7-105">大きな値で署名するよりも、ハッシュ値を使用すれば効率的に署名できます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="8abb7-106">ハッシュ値は、安全でないチャネルを介して送信されたデータの整合性を検証するためにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="8abb7-107">受信したデータのハッシュ値を送信したデータのハッシュ値と比較すると、データが変更されたかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="8abb7-108">このトピックでは、<xref:System.Security.Cryptography?displayProperty=nameWithType> 名前空間のクラスを使用してハッシュ コードの生成と検証を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8abb7-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="8abb7-109">ハッシュの生成</span><span class="sxs-lookup"><span data-stu-id="8abb7-109">Generating a Hash</span></span>  
 <span data-ttu-id="8abb7-110">マネージ ハッシュ クラスでは、バイト配列またはマネージ ストリーム オブジェクトのいずれかをハッシュできます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="8abb7-111">SHA1 ハッシュ アルゴリズムを使用して文字列のハッシュ値を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8abb7-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="8abb7-112">この例では、<xref:System.Text.UnicodeEncoding> クラスを使用して文字列をバイト配列に変換し、<xref:System.Security.Cryptography.SHA1Managed> クラスを使用してバイト配列をハッシュします。</span><span class="sxs-lookup"><span data-stu-id="8abb7-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="8abb7-113">ハッシュ値はコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="8abb7-114">上記のコードは、次の文字列をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="8abb7-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="8abb7-115">ハッシュの検証</span><span class="sxs-lookup"><span data-stu-id="8abb7-115">Verifying a Hash</span></span>  
 <span data-ttu-id="8abb7-116">データをハッシュ値と比較すると、整合性を判断できます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="8abb7-117">通常、データは特定のタイミングでハッシュされ、ハッシュ値はなんらかの方法で保護されます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="8abb7-118">後でデータをもう一度ハッシュし、保護されている値と比較できます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="8abb7-119">ハッシュ値が一致する場合、データは変更されていません。</span><span class="sxs-lookup"><span data-stu-id="8abb7-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="8abb7-120">値が一致しない場合は、データが破損しています。</span><span class="sxs-lookup"><span data-stu-id="8abb7-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="8abb7-121">このシステムを機能させるには、保護されたハッシュを暗号化するか、信頼されていないあらゆる対象に対して内密を保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="8abb7-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="8abb7-122">文字列の前のハッシュ値を新しいハッシュ値と比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8abb7-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="8abb7-123">この例では、ループ処理でハッシュ値の各バイトをすべて比較します。</span><span class="sxs-lookup"><span data-stu-id="8abb7-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="8abb7-124">2 つのハッシュ値が一致する場合は、上記のコードによってコンソールに次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="8abb7-125">一致しない場合は、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="8abb7-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="8abb7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="8abb7-126">See Also</span></span>  
 [<span data-ttu-id="8abb7-127">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="8abb7-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
