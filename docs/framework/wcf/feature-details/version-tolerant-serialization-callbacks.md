---
title: "バージョン トレラントなシリアル化コールバック"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70b89ff741d2a2036d5684ebc4526a6cb7ec49d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="91ccd-102">バージョン トレラントなシリアル化コールバック</span><span class="sxs-lookup"><span data-stu-id="91ccd-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="91ccd-103">データ コントラクトのプログラミング モデルでは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスと <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> クラスがサポートする、複数のバージョンに対応するシリアル化コールバック メソッドが完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="91ccd-104">複数のバージョンに対応する属性</span><span class="sxs-lookup"><span data-stu-id="91ccd-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="91ccd-105">4 つのコールバック属性があります。</span><span class="sxs-lookup"><span data-stu-id="91ccd-105">There are four callback attributes.</span></span> <span data-ttu-id="91ccd-106">各属性は、さまざまなタイミングでシリアル化エンジンまたは逆シリアル化エンジンが呼び出すメソッドに適用できます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="91ccd-107">次の表では、各属性を使用するタイミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="91ccd-108">属性</span><span class="sxs-lookup"><span data-stu-id="91ccd-108">Attribute</span></span>|<span data-ttu-id="91ccd-109">対応するメソッドが呼び出されるタイミング</span><span class="sxs-lookup"><span data-stu-id="91ccd-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="91ccd-110">型をシリアル化する前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="91ccd-111">型をシリアル化した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="91ccd-112">型を逆シリアル化する前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="91ccd-113">型を逆シリアル化した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="91ccd-114">メソッドは、<xref:System.Runtime.Serialization.StreamingContext> パラメーターを受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="91ccd-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="91ccd-115">これらのメソッドは、主にバージョン管理と初期化に使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="91ccd-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="91ccd-116">逆シリアル化時にコンストラクターは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="91ccd-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="91ccd-117">このため、データ メンバーのデータが受信ストリームにない場合、たとえば、データの送信元が、一部のデータ メンバーが不足している前のバージョンの型である場合、そのデータ メンバーを目的の既定値に適切に初期化できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="91ccd-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="91ccd-118">これを修正するには、次の例で示すように、<xref:System.Runtime.Serialization.OnDeserializingAttribute> でマークされたコールバック メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="91ccd-119">上記の各コールバック属性でマークできるのは、型ごとに 1 つのメソッドだけです。</span><span class="sxs-lookup"><span data-stu-id="91ccd-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="91ccd-120">例</span><span class="sxs-lookup"><span data-stu-id="91ccd-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="91ccd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="91ccd-121">See Also</span></span>  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [<span data-ttu-id="91ccd-122">バージョン トレラントなシリアル化</span><span class="sxs-lookup"><span data-stu-id="91ccd-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
