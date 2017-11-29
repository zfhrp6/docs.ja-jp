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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09d43ed76ef70f4478aa1029c254a7b1686a8d08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="bd8bf-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd8bf-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="bd8bf-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd8bf-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="bd8bf-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bd8bf-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bd8bf-105">Methods</span></span>  
 <span data-ttu-id="bd8bf-106">BinaryMessageEncodingBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bd8bf-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bd8bf-107">Properties</span></span>  
 <span data-ttu-id="bd8bf-108">BinaryMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="bd8bf-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="bd8bf-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="bd8bf-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="bd8bf-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd8bf-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bd8bf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd8bf-112">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="bd8bf-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="bd8bf-113">MaxSessionSize</span></span>  
 <span data-ttu-id="bd8bf-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="bd8bf-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd8bf-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bd8bf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd8bf-116">エンコーディングに使用するバッファーのサイズ (バイト単位) を指定する値です。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="bd8bf-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="bd8bf-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="bd8bf-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="bd8bf-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd8bf-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bd8bf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd8bf-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="bd8bf-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="bd8bf-121">ReaderQuotas</span></span>  
 <span data-ttu-id="bd8bf-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="bd8bf-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="bd8bf-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bd8bf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd8bf-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8bf-125">要件</span><span class="sxs-lookup"><span data-stu-id="bd8bf-125">Requirements</span></span>  
  
|<span data-ttu-id="bd8bf-126">MOF</span><span class="sxs-lookup"><span data-stu-id="bd8bf-126">MOF</span></span>|<span data-ttu-id="bd8bf-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="bd8bf-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bd8bf-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="bd8bf-128">Namespace</span></span>|<span data-ttu-id="bd8bf-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="bd8bf-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd8bf-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd8bf-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
