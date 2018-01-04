---
title: "シリアル化プロセスの手順"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c232a76c8a000fcf4ac6c98d3f5c19e50869a362
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="646d2-102">シリアル化プロセスの手順</span><span class="sxs-lookup"><span data-stu-id="646d2-102">Steps in the serialization process</span></span>
<span data-ttu-id="646d2-103">[フォーマッタ](xref:System.Runtime.Serialization.Formatter)で <xref:System.Runtime.Serialization.Formatter.Serialize*> メソッドが呼び出されると、次の一連の規則に従って、オブジェクトのシリアル化プロセスが実行されます。</span><span class="sxs-lookup"><span data-stu-id="646d2-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="646d2-104">フォーマッタにサロゲート セレクターが存在するかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="646d2-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="646d2-105">サロゲート セレクターが存在する場合は、そのサロゲート セレクターが指定された型のオブジェクトを処理できるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="646d2-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="646d2-106">そのオブジェクトの型を処理できる場合は、サロゲート セレクターで <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="646d2-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="646d2-107">サロゲート セレクターが存在しないか、またはサロゲート セレクターがそのオブジェクトの型を処理しない場合は、オブジェクトが [Serializable](xref:System.SerializableAttribute) 属性でマークされているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="646d2-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="646d2-108">オブジェクトにそのマークがない場合、<xref:System.Runtime.Serialization.SerializationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="646d2-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="646d2-109">オブジェクトが適切にマークされている場合は、オブジェクトが <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装しているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="646d2-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="646d2-110">実装している場合は、そのオブジェクトで <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="646d2-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="646d2-111">オブジェクトが <xref:System.Runtime.Serialization.ISerializable> を実装していない場合は、既定のシリアル化ポリシーを適用して、[NonSerialized](xref:System.NonSerializedAttribute) としてマークされていないすべてのフィールドをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="646d2-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="646d2-112">参照</span><span class="sxs-lookup"><span data-stu-id="646d2-112">See Also</span></span>  
 [<span data-ttu-id="646d2-113">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="646d2-113">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="646d2-114">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="646d2-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)