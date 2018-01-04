---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1e026296745f6fc40171866c81f91818789e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="ceb02-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ceb02-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="ceb02-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ceb02-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb02-104">構文</span><span class="sxs-lookup"><span data-stu-id="ceb02-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ceb02-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ceb02-105">Methods</span></span>  
 <span data-ttu-id="ceb02-106">TextMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="ceb02-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ceb02-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ceb02-107">Properties</span></span>  
 <span data-ttu-id="ceb02-108">TextMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ceb02-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="ceb02-109">エンコード</span><span class="sxs-lookup"><span data-stu-id="ceb02-109">Encoding</span></span>  
 <span data-ttu-id="ceb02-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ceb02-110">Data type: string</span></span>  
  
 <span data-ttu-id="ceb02-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ceb02-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb02-112">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="ceb02-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="ceb02-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ceb02-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="ceb02-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ceb02-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ceb02-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ceb02-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb02-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="ceb02-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="ceb02-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ceb02-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="ceb02-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ceb02-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ceb02-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ceb02-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb02-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="ceb02-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="ceb02-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ceb02-121">ReaderQuotas</span></span>  
 <span data-ttu-id="ceb02-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ceb02-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="ceb02-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ceb02-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ceb02-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="ceb02-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceb02-125">要件</span><span class="sxs-lookup"><span data-stu-id="ceb02-125">Requirements</span></span>  
  
|<span data-ttu-id="ceb02-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ceb02-126">MOF</span></span>|<span data-ttu-id="ceb02-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ceb02-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ceb02-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="ceb02-128">Namespace</span></span>|<span data-ttu-id="ceb02-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ceb02-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceb02-130">参照</span><span class="sxs-lookup"><span data-stu-id="ceb02-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
