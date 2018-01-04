---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a3afb9b8cfede60c773d146f4d1728d7fe02b75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="1461a-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1461a-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="1461a-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1461a-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1461a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1461a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1461a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1461a-105">Methods</span></span>  
 <span data-ttu-id="1461a-106">XmlDictionaryReaderQuotas クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="1461a-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1461a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1461a-107">Properties</span></span>  
 <span data-ttu-id="1461a-108">XmlDictionaryReaderQuotas クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1461a-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="1461a-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="1461a-109">MaxArrayLength</span></span>  
 <span data-ttu-id="1461a-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="1461a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="1461a-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1461a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1461a-112">許される最大配列長。</span><span class="sxs-lookup"><span data-stu-id="1461a-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="1461a-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="1461a-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="1461a-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="1461a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1461a-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1461a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1461a-116">1 回の読み取りで返すことができる最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="1461a-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="1461a-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="1461a-117">MaxDepth</span></span>  
 <span data-ttu-id="1461a-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="1461a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1461a-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1461a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1461a-120">1 回の読み取りでの最大ネスト ノード深度。</span><span class="sxs-lookup"><span data-stu-id="1461a-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="1461a-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="1461a-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="1461a-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="1461a-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="1461a-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1461a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1461a-124">テーブル名の最大文字数。</span><span class="sxs-lookup"><span data-stu-id="1461a-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="1461a-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="1461a-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="1461a-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="1461a-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="1461a-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1461a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1461a-128">XML 要素のコンテンツで許可される最大文字数。</span><span class="sxs-lookup"><span data-stu-id="1461a-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1461a-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="1461a-129">Requirements</span></span>  
  
|<span data-ttu-id="1461a-130">MOF</span><span class="sxs-lookup"><span data-stu-id="1461a-130">MOF</span></span>|<span data-ttu-id="1461a-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="1461a-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1461a-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="1461a-132">Namespace</span></span>|<span data-ttu-id="1461a-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="1461a-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1461a-134">参照</span><span class="sxs-lookup"><span data-stu-id="1461a-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
