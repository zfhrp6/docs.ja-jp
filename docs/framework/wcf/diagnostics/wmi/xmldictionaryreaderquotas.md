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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 980a7eacd095dc1b601d63f5a807f2e287c09885
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="f4b28-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f4b28-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="f4b28-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f4b28-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b28-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4b28-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f4b28-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f4b28-105">Methods</span></span>  
 <span data-ttu-id="f4b28-106">XmlDictionaryReaderQuotas クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="f4b28-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f4b28-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f4b28-107">Properties</span></span>  
 <span data-ttu-id="f4b28-108">XmlDictionaryReaderQuotas クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="f4b28-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="f4b28-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="f4b28-109">MaxArrayLength</span></span>  
 <span data-ttu-id="f4b28-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="f4b28-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f4b28-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f4b28-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4b28-112">許される最大配列長。</span><span class="sxs-lookup"><span data-stu-id="f4b28-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="f4b28-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="f4b28-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="f4b28-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="f4b28-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f4b28-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f4b28-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4b28-116">1 回の読み取りで返すことができる最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="f4b28-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="f4b28-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="f4b28-117">MaxDepth</span></span>  
 <span data-ttu-id="f4b28-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="f4b28-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f4b28-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f4b28-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4b28-120">1 回の読み取りでの最大ネスト ノード深度。</span><span class="sxs-lookup"><span data-stu-id="f4b28-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="f4b28-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="f4b28-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="f4b28-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="f4b28-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="f4b28-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f4b28-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4b28-124">テーブル名の最大文字数。</span><span class="sxs-lookup"><span data-stu-id="f4b28-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="f4b28-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="f4b28-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="f4b28-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="f4b28-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="f4b28-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f4b28-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4b28-128">XML 要素のコンテンツで許可される最大文字数。</span><span class="sxs-lookup"><span data-stu-id="f4b28-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4b28-129">要件</span><span class="sxs-lookup"><span data-stu-id="f4b28-129">Requirements</span></span>  
  
|<span data-ttu-id="f4b28-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f4b28-130">MOF</span></span>|<span data-ttu-id="f4b28-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="f4b28-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f4b28-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="f4b28-132">Namespace</span></span>|<span data-ttu-id="f4b28-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="f4b28-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4b28-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4b28-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
