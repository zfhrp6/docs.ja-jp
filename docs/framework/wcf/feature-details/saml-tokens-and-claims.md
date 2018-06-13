---
title: SAML トークンとクレーム
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: 374fde23a1bf8df704f76500b4808c16d142ddd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494733"
---
# <a name="saml-tokens-and-claims"></a>SAML トークンとクレーム
Security Assertions Markup Language (SAML)*トークン*はクレームの XML 表現。 フェデレーション セキュリティ シナリオで Windows Communication Foundation (WCF) を使用して SAML トークンは、既定では、*発行済みトークン*です。  
  
 SAML トークンは、ステートメント (特定のエンティティによって他のエンティティに関して作成されるクレームのセット) を伝達します。 たとえば、フェデレーション セキュリティ シナリオでは、ステートメントがセキュリティ トークン サービスによって、システム内の特定のユーザーに関して作成されます。 セキュリティ トークン サービスは、トークンに含まれるステートメントの信憑性を示すために SAML トークンに署名します。 また、SAML トークンは、SAML トークンのユーザーが証明として提示する暗号化キー マテリアルに関連付けられています。 これが証拠となり、証明書利用者は、SAML トークンが実際にそのユーザーに対して発行されたことを確認できます。 一般的なシナリオでの例を次に示します。  
  
1.  クライアントは、セキュリティ トークン サービスから SAML トークンを要求し、Windows 資格情報を使用して、そのセキュリティ トークン サービスに対して認証を行います。  
  
2.  セキュリティ トークン サービスは、SAML トークンをクライアントに発行します。 SAML トークンは、セキュリティ トークン サービスに関連付けられた証明書を使用して署名され、ターゲット サービス用に暗号化された証明キーを含んでいます。  
  
3.  クライアントものコピーを受け取る、*証明キー*です。 クライアント アプリケーション サービスを SAML トークンを提示し、(、*証明書利用者*) し、その証明キーを持つメッセージに署名します。  
  
4.  SAML トークンの署名は、そのトークンがセキュリティ トークン サービスによって発行されたことを証明書利用者に示します。 また、証明キーを使用して作成されたメッセージ署名は、トークンがそのクライアントに対して発行されたことを示します。  
  
## <a name="from-claims-to-samlattributes"></a>クレームから SamlAttributes  
 WCF では、SAML トークン内のステートメントとしてモデル化<xref:System.IdentityModel.Tokens.SamlAttribute>から直接データを読み込むことができます、オブジェクト<xref:System.IdentityModel.Claims.Claim>用意されているオブジェクト、<xref:System.IdentityModel.Claims.Claim>オブジェクトには、<xref:System.IdentityModel.Claims.Claim.Right%2A>のプロパティ<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>と<xref:System.IdentityModel.Claims.Claim.Resource%2A>プロパティは、型<xref:System.String>です。 例えば:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  セキュリティ トークン サービスによって発行されたか、または認証の一部としてクライアントからサービスに提示されたときに、SAML トークンがメッセージ内にシリアル化される場合、メッセージの最大クォータ サイズが、SAML トークンおよびメッセージの他の部分を格納できるだけの大きさである必要があります。 通常は、既定のメッセージ クォータ サイズで十分です。 ただし、何百ものクレームを含んでいるために SAML トークンのサイズが大きい場合には、シリアル化されたトークンを格納できるように、クォータを増やす必要が生じることがあります。 詳細については、次を参照してください。[データのセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)です。  
  
## <a name="from-samlattributes-to-claims"></a>SamlAttributes からクレーム  
 SAML トークンがメッセージで受信されると、SAML トークン内のさまざまなステートメントは、 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> オブジェクトに変換され、<xref:System.IdentityModel.Policy.AuthorizationContext> に配置されます。 各 SAML ステートメントのクレームは <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> の <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティによって返され、これを調べることによってユーザーの認証と承認を行うかどうかを決定できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)  
 [方法 : フェデレーション クライアントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [クレームとトークン](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [クレームの作成とリソース値](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [方法 : カスタム クレームを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
