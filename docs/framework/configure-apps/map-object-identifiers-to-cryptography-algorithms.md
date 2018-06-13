---
title: 暗号化アルゴリズムへのオブジェクト ID の割り当て
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7801c55cf6b3334347788013d9052038d5d2f3ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756619"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="af7b5-102">暗号化アルゴリズムへのオブジェクト ID の割り当て</span><span class="sxs-lookup"><span data-stu-id="af7b5-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="af7b5-103">デジタル署名は、データが改ざんされない 1 つのプログラムから別の送信時を確認します。</span><span class="sxs-lookup"><span data-stu-id="af7b5-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="af7b5-104">通常、デジタル署名は、数学関数に署名するデータのハッシュを適用して計算されます。</span><span class="sxs-lookup"><span data-stu-id="af7b5-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="af7b5-105">署名するハッシュ値を書式設定時に一部のデジタル署名アルゴリズムは、書式設定操作の一部として ASN.1 オブジェクト識別子 (OID) を追加します。</span><span class="sxs-lookup"><span data-stu-id="af7b5-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="af7b5-106">OID は、ハッシュの計算に使用されたアルゴリズムを識別します。</span><span class="sxs-lookup"><span data-stu-id="af7b5-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="af7b5-107">アルゴリズムは、カスタム アルゴリズムを使用する暗号化機構を拡張するオブジェクトの識別子にマップできます。</span><span class="sxs-lookup"><span data-stu-id="af7b5-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="af7b5-108">次の例では、オブジェクト識別子を新しいハッシュ アルゴリズムにマップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af7b5-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="af7b5-109">[ \<OidEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)2 つの属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="af7b5-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="af7b5-110">**OID**属性は、オブジェクトの識別番号。</span><span class="sxs-lookup"><span data-stu-id="af7b5-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="af7b5-111">**名前**属性の値が、**名前**属性から、 [ \<nameEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7b5-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="af7b5-112">オブジェクト識別子は、簡易名にマップできる前に、クラスにアルゴリズム名をマッピングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="af7b5-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7b5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="af7b5-113">See Also</span></span>  
 [<span data-ttu-id="af7b5-114">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="af7b5-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="af7b5-115">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="af7b5-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
