---
title: "方法 : カスタム クレームを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : カスタム クレームを作成する
Id モデル インフラストラクチャで[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]ヘルパー関数を作成するための組み込みクレームの種類と権限のセットを提供<xref:System.IdentityModel.Claims.Claim>その種類と権限を持つインスタンス。 この組み込みクレームは、既定で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をサポートするクライアント資格情報の型内にある情報をモデル化するように作成されています。 多くの場合はこの組み込みクレームで十分ですが、一部のアプリケーションでカスタム クレームが必要になる場合があります。 クレームは、クレームが適用されるリソースを示すクレームの種類と、リソースにアサートされる権限で構成されます。 このトピックでは、カスタム クレームを作成する方法について説明します。  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>プリミティブ データ型に基づくカスタム クレームを作成するには  
  
1.  クレームの種類、リソースの値とする権利を渡すことによって、カスタム クレームを作成、 <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>コンス トラクターです。  
  
    1.  クレームの種類の一意の値を指定します。  
  
         クレームの種類は一意の文字列識別子です。 カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。 定義されているクレームの種類の一覧については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください、 <xref:System.IdentityModel.Claims.ClaimTypes>クラスです。  
  
    2.  プリミティブ データ型とリソースの値を選択します。  
  
         リソースはオブジェクトです。 リソースの CLR 型では、プリミティブをなど、<xref:System.String>または<xref:System.Int32>、または任意のシリアル化可能な型です。 クレームは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によりさまざまな点でシリアル化されるため、CLR 型のリソースはシリアル化可能なものにする必要があります。 プリミティブ型はシリアル化できます。  
  
    3.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で定義されている権限か、カスタム権限の一意の値を選択します。  
  
         権限は一意の文字列識別子です。 定義されている権利[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]で定義された、<xref:System.IdentityModel.Claims.Rights>クラスです。  
  
         カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。  
  
         次のコード例では、カスタム クレームを作成の要求の種類で`http://example.org/claims/simplecustomclaim`、という名前のリソースの`Driver's License`を使用して、 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>適切です。  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>プリミティブ以外のデータ型に基づくカスタム クレームを作成するには  
  
1.  クレームの種類、リソースの値とする権利を渡すことによって、カスタム クレームを作成、 <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>コンス トラクターです。  
  
    1.  クレームの種類の一意の値を指定します。  
  
         クレームの種類は一意の文字列識別子です。 カスタム クレームを作成する場合、クレームの種類に使用されている文字列識別子が一意になるようにしてください。 定義されているクレームの種類の一覧については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください、 <xref:System.IdentityModel.Claims.ClaimTypes>クラスです。  
  
    2.  リソース用のシリアル化可能な、プリミティブ型以外の型を選択または定義します。  
  
         リソースはオブジェクトです。 クレームは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によりさまざまな点でシリアル化されるため、CLR 型のリソースはシリアル化可能なものにする必要があります。 プリミティブ型は既にシリアル化できます。  
  
         新しい型が定義されている場合は、適用、 <xref:System.Runtime.Serialization.DataContractAttribute>クラスにします。 適用も、 <xref:System.Runtime.Serialization.DataMemberAttribute>属性をクレームの一部としてシリアル化する必要のある新しい型のすべてのメンバーにします。  
  
         `MyResourceType` というカスタム リソース型を定義するコード例を次に示します。  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         <!-- TODO: review snippet reference [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]  -->  
  
    3.  
          [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で定義されている権限か、カスタム権限の一意の値を選択します。  
  
         権限は一意の文字列識別子です。 定義されている権利[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]で定義された、<xref:System.IdentityModel.Claims.Rights>クラスです。  
  
         カスタム クレームを作成する場合、権限に使用されている文字列識別子が一意になるようにしてください。  
  
         次のコード例では、カスタム クレームを作成の要求の種類で`http://example.org/claims/complexcustomclaim`、カスタム リソース型`MyResourceType`を使用して、 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>右です。  
  
     [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
     <!-- TODO: review snippet reference [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]  -->  
  
## <a name="example"></a>例  
 次のコード例で、プリミティブ リソース型を持つカスタム クレームと、プリミティブ以外のリソース型を持つカスタム クレームの作成方法を示します。  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Claims.Claim>   
 <xref:System.IdentityModel.Claims.Rights>   
 <xref:System.IdentityModel.Claims.ClaimTypes>   
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 [クレームと Id モデルの承認を管理します。](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [クレームと Id モデルの承認を管理します。](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)