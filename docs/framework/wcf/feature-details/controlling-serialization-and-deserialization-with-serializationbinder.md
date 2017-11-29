---
title: "SerializationBinder を使用したシリアル化および逆シリアル化の制御"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="b04f0-102">SerializationBinder を使用したシリアル化および逆シリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="b04f0-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="b04f0-103">シリアル化中に、フォーマッタは、正しい型およびバージョンのオブジェクトのインスタンスを作成するために必要な情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="b04f0-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="b04f0-104">通常、この情報には、オブジェクトの完全な型名および完全なアセンブリ名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b04f0-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="b04f0-105">既定では、逆シリアル化でこの情報を使用して、同一のオブジェクトのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b04f0-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="b04f0-106">場合によっては、シリアル化するクラスと逆シリアル化するクラスの制御が必要となります。これは、元のクラスが逆シリアル化を実行するコンピューター上に存在していない可能性がある場合、元のクラスがアセンブリ間で移動されている場合、または、サーバー上とクライアント上では異なるバージョンのクラスが必要である場合です。</span><span class="sxs-lookup"><span data-stu-id="b04f0-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b04f0-107">[シリアル化バインダーの使用法](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)です。</span><span class="sxs-lookup"><span data-stu-id="b04f0-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b04f0-108">この機能は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> または <xref:System.Runtime.Serialization.NetDataContractSerializer> を使用してのみ、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="b04f0-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="b04f0-109">SerializationBinder の使用</span><span class="sxs-lookup"><span data-stu-id="b04f0-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="b04f0-110"><xref:System.Runtime.Serialization.SerializationBinder> は、シリアル化中および逆シリアル化中に使用される実際の型を制御するために使用される抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="b04f0-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="b04f0-111">シリアル化および逆シリアル化中に使用される型を制御するには、派生クラスを<xref:System.Runtime.Serialization.SerializationBinder>をオーバーライドし、 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String、System.String)?qualifyHint=False & autoUpgrade = True と<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>System.String)?qualifyHint = False & autoUpgrade = True メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b04f0-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True methods.</span></span> <span data-ttu-id="b04f0-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String、System.String)?qualifyHint=False & autoUpgrade = True メソッドは、<xref:System.Type>し、アセンブリと型名を返します。</span><span class="sxs-lookup"><span data-stu-id="b04f0-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="b04f0-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = True メソッドはアセンブリと型名を返します、<xref:System.Type>です。</span><span class="sxs-lookup"><span data-stu-id="b04f0-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04f0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b04f0-114">See Also</span></span>  
 [<span data-ttu-id="b04f0-115">シリアル化および逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="b04f0-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="b04f0-116">シリアル化バインダーの使用法</span><span class="sxs-lookup"><span data-stu-id="b04f0-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
