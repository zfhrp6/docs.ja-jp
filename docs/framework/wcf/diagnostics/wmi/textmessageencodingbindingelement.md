---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: f9b94e946413967cc14282e85743a23327683b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="c2cda-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c2cda-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="c2cda-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c2cda-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2cda-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2cda-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c2cda-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c2cda-105">Methods</span></span>  
 <span data-ttu-id="c2cda-106">TextMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="c2cda-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c2cda-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c2cda-107">Properties</span></span>  
 <span data-ttu-id="c2cda-108">TextMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c2cda-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="c2cda-109">エンコード</span><span class="sxs-lookup"><span data-stu-id="c2cda-109">Encoding</span></span>  
 <span data-ttu-id="c2cda-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="c2cda-110">Data type: string</span></span>  
  
 <span data-ttu-id="c2cda-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c2cda-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2cda-112">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="c2cda-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="c2cda-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c2cda-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="c2cda-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="c2cda-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c2cda-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c2cda-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2cda-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="c2cda-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="c2cda-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c2cda-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="c2cda-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="c2cda-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c2cda-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c2cda-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2cda-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="c2cda-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="c2cda-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c2cda-121">ReaderQuotas</span></span>  
 <span data-ttu-id="c2cda-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c2cda-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="c2cda-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c2cda-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2cda-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="c2cda-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2cda-125">要件</span><span class="sxs-lookup"><span data-stu-id="c2cda-125">Requirements</span></span>  
  
|<span data-ttu-id="c2cda-126">MOF</span><span class="sxs-lookup"><span data-stu-id="c2cda-126">MOF</span></span>|<span data-ttu-id="c2cda-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c2cda-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c2cda-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="c2cda-128">Namespace</span></span>|<span data-ttu-id="c2cda-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c2cda-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2cda-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2cda-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
