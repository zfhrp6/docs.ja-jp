---
title: "方法 : カスタム クレームを作成する"
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
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0cc23d5b6720d78afdc1acd50a2b84b76b977e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="148f0-102">方法 : カスタム クレームを作成する</span><span class="sxs-lookup"><span data-stu-id="148f0-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="148f0-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の ID モデル インフラストラクチャでは、一連の組み込みクレームの種類と権限、およびその種類と権限を使用して <xref:System.IdentityModel.Claims.Claim> インスタンスを作成するヘルパー関数が提供されます。</span><span class="sxs-lookup"><span data-stu-id="148f0-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="148f0-104">この組み込みクレームは、既定で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をサポートするクライアント資格情報の型内にある情報をモデル化するように作成されています。</span><span class="sxs-lookup"><span data-stu-id="148f0-104">These built-in claims are designed to model information found in client credential types that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports by default.</span></span> <span data-ttu-id="148f0-105">多くの場合はこの組み込みクレームで十分ですが、一部のアプリケーションでカスタム クレームが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="148f0-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="148f0-106">クレームは、クレームが適用されるリソースを示すクレームの種類と、リソースにアサートされる権限で構成されます。</span><span class="sxs-lookup"><span data-stu-id="148f0-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="148f0-107">このトピックでは、カスタム クレームを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="148f0-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="148f0-108">プリミティブ データ型に基づくカスタム クレームを作成するには</span><span class="sxs-lookup"><span data-stu-id="148f0-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="148f0-109">クレームの種類、リソースの値、<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> コンストラクターへの権限を渡すことで、カスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="148f0-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="148f0-110">クレームの種類の一意の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="148f0-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="148f0-111">クレームの種類は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="148f0-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="148f0-112">カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="148f0-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="148f0-113">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって定義されたクレームの種類の一覧については、<xref:System.IdentityModel.Claims.ClaimTypes> クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="148f0-113">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="148f0-114">プリミティブ データ型とリソースの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="148f0-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="148f0-115">リソースはオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="148f0-115">A resource is an object.</span></span> <span data-ttu-id="148f0-116">CLR 型のリソースにはプリミティブを指定できます。たとえば、<xref:System.String> や <xref:System.Int32>、または任意のシリアル化可能な型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="148f0-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="148f0-117">クレームは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によりさまざまな点でシリアル化されるため、CLR 型のリソースはシリアル化可能なものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="148f0-117">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="148f0-118">プリミティブ型はシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="148f0-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="148f0-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で定義されている権限か、カスタム権限の一意の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="148f0-119">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="148f0-120">権限は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="148f0-120">A right is a unique string identifier.</span></span> <span data-ttu-id="148f0-121">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で定義された権限は <xref:System.IdentityModel.Claims.Rights> クラスで定義されています。</span><span class="sxs-lookup"><span data-stu-id="148f0-121">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="148f0-122">カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="148f0-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="148f0-123">次のコード例では、`http://example.org/claims/simplecustomclaim` という名前のリソース用の `Driver's License` というクレームの種類と <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限を持つカスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="148f0-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="148f0-124">プリミティブ以外のデータ型に基づくカスタム クレームを作成するには</span><span class="sxs-lookup"><span data-stu-id="148f0-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="148f0-125">クレームの種類、リソースの値、<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> コンストラクターへの権限を渡すことで、カスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="148f0-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="148f0-126">クレームの種類の一意の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="148f0-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="148f0-127">クレームの種類は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="148f0-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="148f0-128">カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="148f0-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="148f0-129">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって定義されたクレームの種類の一覧については、<xref:System.IdentityModel.Claims.ClaimTypes> クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="148f0-129">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="148f0-130">リソース用のシリアル化可能な、プリミティブ型以外の型を選択または定義します。</span><span class="sxs-lookup"><span data-stu-id="148f0-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="148f0-131">リソースはオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="148f0-131">A resource is an object.</span></span> <span data-ttu-id="148f0-132">クレームは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によりさまざまな点でシリアル化されるため、CLR 型のリソースはシリアル化可能なものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="148f0-132">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="148f0-133">プリミティブ型は既にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="148f0-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="148f0-134">新しい型を作成する場合は、<xref:System.Runtime.Serialization.DataContractAttribute> をクラスに適用します。</span><span class="sxs-lookup"><span data-stu-id="148f0-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="148f0-135">また、クレームの一部としてシリアル化する必要のある新しい型のすべてのメンバーにも <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="148f0-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="148f0-136">`MyResourceType` というカスタム リソース型を定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="148f0-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="148f0-137">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で定義されている権限か、カスタム権限の一意の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="148f0-137">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="148f0-138">権限は一意の文字列識別子です。</span><span class="sxs-lookup"><span data-stu-id="148f0-138">A right is a unique string identifier.</span></span> <span data-ttu-id="148f0-139">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で定義された権限は <xref:System.IdentityModel.Claims.Rights> クラスで定義されています。</span><span class="sxs-lookup"><span data-stu-id="148f0-139">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="148f0-140">カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="148f0-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="148f0-141">次のコード例では、`http://example.org/claims/complexcustomclaim` というクレームの種類 (`MyResourceType` カスタム リソース型) および <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限を持つカスタム クレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="148f0-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="148f0-142">例</span><span class="sxs-lookup"><span data-stu-id="148f0-142">Example</span></span>  
 <span data-ttu-id="148f0-143">次のコード例で、プリミティブ リソース型を持つカスタム クレームと、プリミティブ以外のリソース型を持つカスタム クレームの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="148f0-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="148f0-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="148f0-144">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="148f0-145">クレームと Id モデルによる承認の管理</span><span class="sxs-lookup"><span data-stu-id="148f0-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="148f0-146">クレームと Id モデルによる承認の管理</span><span class="sxs-lookup"><span data-stu-id="148f0-146">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
