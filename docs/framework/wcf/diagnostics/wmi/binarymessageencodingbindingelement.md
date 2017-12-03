---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="4a4c7-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4a4c7-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="4a4c7-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4a4c7-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a4c7-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4a4c7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4a4c7-105">Methods</span></span>  
 <span data-ttu-id="4a4c7-106">BinaryMessageEncodingBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a4c7-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4a4c7-107">Properties</span></span>  
 <span data-ttu-id="4a4c7-108">BinaryMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="4a4c7-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4a4c7-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4a4c7-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="4a4c7-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a4c7-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4a4c7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a4c7-112">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="4a4c7-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="4a4c7-113">MaxSessionSize</span></span>  
 <span data-ttu-id="4a4c7-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="4a4c7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a4c7-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4a4c7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a4c7-116">エンコーディングに使用するバッファーのサイズ (バイト単位) を指定する値です。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="4a4c7-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4a4c7-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4a4c7-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="4a4c7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a4c7-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4a4c7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a4c7-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="4a4c7-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4a4c7-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4a4c7-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4a4c7-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4a4c7-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4a4c7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a4c7-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a4c7-125">要件</span><span class="sxs-lookup"><span data-stu-id="4a4c7-125">Requirements</span></span>  
  
|<span data-ttu-id="4a4c7-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4a4c7-126">MOF</span></span>|<span data-ttu-id="4a4c7-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="4a4c7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4a4c7-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="4a4c7-128">Namespace</span></span>|<span data-ttu-id="4a4c7-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="4a4c7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a4c7-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a4c7-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
