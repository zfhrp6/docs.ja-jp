---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 78914d52a9e57fe2e48adcfc0d7b6f911a0d8b3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487829"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="5b5d2-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="5b5d2-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="5b5d2-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="5b5d2-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5d2-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b5d2-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5b5d2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5b5d2-105">Methods</span></span>  
 <span data-ttu-id="5b5d2-106">XmlDictionaryReaderQuotas クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5b5d2-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5b5d2-107">Properties</span></span>  
 <span data-ttu-id="5b5d2-108">XmlDictionaryReaderQuotas クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="5b5d2-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="5b5d2-109">MaxArrayLength</span></span>  
 <span data-ttu-id="5b5d2-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5b5d2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="5b5d2-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b5d2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b5d2-112">許される最大配列長。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="5b5d2-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="5b5d2-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="5b5d2-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5b5d2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="5b5d2-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b5d2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b5d2-116">1 回の読み取りで返すことができる最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="5b5d2-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="5b5d2-117">MaxDepth</span></span>  
 <span data-ttu-id="5b5d2-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5b5d2-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="5b5d2-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b5d2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b5d2-120">1 回の読み取りでの最大ネスト ノード深度。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="5b5d2-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="5b5d2-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="5b5d2-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5b5d2-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="5b5d2-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b5d2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b5d2-124">テーブル名の最大文字数。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="5b5d2-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="5b5d2-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="5b5d2-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5b5d2-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="5b5d2-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b5d2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b5d2-128">XML 要素のコンテンツで許可される最大文字数。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b5d2-129">要件</span><span class="sxs-lookup"><span data-stu-id="5b5d2-129">Requirements</span></span>  
  
|<span data-ttu-id="5b5d2-130">MOF</span><span class="sxs-lookup"><span data-stu-id="5b5d2-130">MOF</span></span>|<span data-ttu-id="5b5d2-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="5b5d2-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5b5d2-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="5b5d2-132">Namespace</span></span>|<span data-ttu-id="5b5d2-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="5b5d2-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b5d2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b5d2-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
