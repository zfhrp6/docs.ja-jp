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
ms.openlocfilehash: be5faf5e465eeacc190081c22d7bc59c3caf5825
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="17609-102">SerializationBinder を使用したシリアル化および逆シリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="17609-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="17609-103">シリアル化中に、フォーマッタは、正しい型およびバージョンのオブジェクトのインスタンスを作成するために必要な情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="17609-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="17609-104">通常、この情報には、オブジェクトの完全な型名および完全なアセンブリ名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17609-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="17609-105">既定では、逆シリアル化でこの情報を使用して、同一のオブジェクトのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="17609-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="17609-106">場合によっては、シリアル化するクラスと逆シリアル化するクラスの制御が必要となります。これは、元のクラスが逆シリアル化を実行するコンピューター上に存在していない可能性がある場合、元のクラスがアセンブリ間で移動されている場合、または、サーバー上とクライアント上では異なるバージョンのクラスが必要である場合です。</span><span class="sxs-lookup"><span data-stu-id="17609-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="17609-107">[シリアル化バインダーの使用法](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)です。</span><span class="sxs-lookup"><span data-stu-id="17609-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="17609-108">この機能は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> または <xref:System.Runtime.Serialization.NetDataContractSerializer> を使用してのみ、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="17609-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="17609-109">SerializationBinder の使用</span><span class="sxs-lookup"><span data-stu-id="17609-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="17609-110"><xref:System.Runtime.Serialization.SerializationBinder> は、シリアル化中および逆シリアル化中に使用される実際の型を制御するために使用される抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="17609-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="17609-111">シリアル化中および逆シリアル化中に使用される型を制御するには、<xref:System.Runtime.Serialization.SerializationBinder> の派生クラスを作成し、<xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> メソッドと <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="17609-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> methods.</span></span> <span data-ttu-id="17609-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> メソッドは <xref:System.Type> を受け取り、アセンブリと型名を返します。</span><span class="sxs-lookup"><span data-stu-id="17609-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="17609-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> メソッドはアセンブリと型名を受け取り、<xref:System.Type> を返します。</span><span class="sxs-lookup"><span data-stu-id="17609-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17609-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="17609-114">See Also</span></span>  
 [<span data-ttu-id="17609-115">シリアル化および逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="17609-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="17609-116">シリアル化バインダーの使用法</span><span class="sxs-lookup"><span data-stu-id="17609-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
