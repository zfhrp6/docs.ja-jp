---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 867b4a2b84a28dff4e3b9e4fc9d3c52065de212f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="a06e0-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="a06e0-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="a06e0-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="a06e0-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="a06e0-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a06e0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a06e0-105">Methods</span></span>  
 <span data-ttu-id="a06e0-106">MtomMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="a06e0-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a06e0-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a06e0-107">Properties</span></span>  
 <span data-ttu-id="a06e0-108">MtomMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a06e0-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="a06e0-109">エンコード</span><span class="sxs-lookup"><span data-stu-id="a06e0-109">Encoding</span></span>  
 <span data-ttu-id="a06e0-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="a06e0-110">Data type: string</span></span>  
  
 <span data-ttu-id="a06e0-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a06e0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a06e0-112">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="a06e0-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="a06e0-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a06e0-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="a06e0-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="a06e0-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="a06e0-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a06e0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a06e0-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="a06e0-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="a06e0-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a06e0-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="a06e0-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="a06e0-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a06e0-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a06e0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a06e0-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="a06e0-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="a06e0-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="a06e0-121">ReaderQuotas</span></span>  
 <span data-ttu-id="a06e0-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="a06e0-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="a06e0-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a06e0-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a06e0-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="a06e0-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a06e0-125">要件</span><span class="sxs-lookup"><span data-stu-id="a06e0-125">Requirements</span></span>  
  
|<span data-ttu-id="a06e0-126">MOF</span><span class="sxs-lookup"><span data-stu-id="a06e0-126">MOF</span></span>|<span data-ttu-id="a06e0-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="a06e0-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a06e0-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="a06e0-128">Namespace</span></span>|<span data-ttu-id="a06e0-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="a06e0-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a06e0-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a06e0-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
