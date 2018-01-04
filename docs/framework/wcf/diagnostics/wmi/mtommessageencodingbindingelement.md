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
ms.workload: dotnet
ms.openlocfilehash: 3cc36d7daed1a2cfaf050cbfe9661951117ff66d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="8e318-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8e318-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="8e318-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8e318-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e318-104">構文</span><span class="sxs-lookup"><span data-stu-id="8e318-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8e318-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8e318-105">Methods</span></span>  
 <span data-ttu-id="8e318-106">MtomMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="8e318-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8e318-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e318-107">Properties</span></span>  
 <span data-ttu-id="8e318-108">MtomMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8e318-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="8e318-109">エンコード</span><span class="sxs-lookup"><span data-stu-id="8e318-109">Encoding</span></span>  
 <span data-ttu-id="8e318-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8e318-110">Data type: string</span></span>  
  
 <span data-ttu-id="8e318-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e318-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e318-112">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="8e318-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="8e318-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8e318-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="8e318-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8e318-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8e318-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e318-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e318-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="8e318-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="8e318-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8e318-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="8e318-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8e318-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8e318-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e318-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e318-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="8e318-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="8e318-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8e318-121">ReaderQuotas</span></span>  
 <span data-ttu-id="8e318-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8e318-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="8e318-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e318-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e318-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="8e318-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e318-125">要件</span><span class="sxs-lookup"><span data-stu-id="8e318-125">Requirements</span></span>  
  
|<span data-ttu-id="8e318-126">MOF</span><span class="sxs-lookup"><span data-stu-id="8e318-126">MOF</span></span>|<span data-ttu-id="8e318-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8e318-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8e318-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="8e318-128">Namespace</span></span>|<span data-ttu-id="8e318-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8e318-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e318-130">参照</span><span class="sxs-lookup"><span data-stu-id="8e318-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
