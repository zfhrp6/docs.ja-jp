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
ms.openlocfilehash: 966f1ae06f5d7e0dacb8b7d450463c75f783ef1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="8c776-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8c776-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="8c776-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8c776-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c776-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c776-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8c776-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c776-105">Methods</span></span>  
 <span data-ttu-id="8c776-106">TextMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="8c776-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8c776-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c776-107">Properties</span></span>  
 <span data-ttu-id="8c776-108">TextMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8c776-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="8c776-109">エンコード</span><span class="sxs-lookup"><span data-stu-id="8c776-109">Encoding</span></span>  
 <span data-ttu-id="8c776-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8c776-110">Data type: string</span></span>  
  
 <span data-ttu-id="8c776-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c776-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c776-112">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="8c776-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="8c776-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8c776-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="8c776-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8c776-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8c776-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c776-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c776-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="8c776-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="8c776-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8c776-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="8c776-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8c776-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8c776-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c776-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c776-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="8c776-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="8c776-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8c776-121">ReaderQuotas</span></span>  
 <span data-ttu-id="8c776-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8c776-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="8c776-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c776-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c776-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="8c776-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c776-125">要件</span><span class="sxs-lookup"><span data-stu-id="8c776-125">Requirements</span></span>  
  
|<span data-ttu-id="8c776-126">MOF</span><span class="sxs-lookup"><span data-stu-id="8c776-126">MOF</span></span>|<span data-ttu-id="8c776-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8c776-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8c776-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="8c776-128">Namespace</span></span>|<span data-ttu-id="8c776-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8c776-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c776-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c776-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
