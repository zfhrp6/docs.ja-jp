---
title: WCF での認証
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: a4f9b719024db1334b599f0f02fe01bc083bf3c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489112"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="dc7a7-102">WCF での認証</span><span class="sxs-lookup"><span data-stu-id="dc7a7-102">Authentication in WCF</span></span>
<span data-ttu-id="dc7a7-103">次のトピックでは、たとえば、認証を提供する Windows Communication Foundation (WCF)、Windows 認証、X.509 証明書、およびユーザー名およびパスワードで多くの異なるメカニズムを表示します。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc7a7-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dc7a7-104">In This Section</span></span>  
 [<span data-ttu-id="dc7a7-105">方法 : ASP.NET メンバーシップ プロバイダーを使用する</span><span class="sxs-lookup"><span data-stu-id="dc7a7-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="dc7a7-106">ASP.NET の機能には、メンバーシップとロール プロバイダー、認証のためのユーザー名とパスワードの組み合わせを格納するデータベース、および承認のためのユーザー ロールがあります。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="dc7a7-107">このトピックでは、WCF サービスが、同じデータベースを使用して、ユーザー認証および承認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="dc7a7-108">方法 : カスタム ユーザー名およびパスワード検証を使用する</span><span class="sxs-lookup"><span data-stu-id="dc7a7-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="dc7a7-109">カスタム ユーザー名およびパスワード検証を統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="dc7a7-110">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="dc7a7-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="dc7a7-111">追加の保護手段として、クライアントは、予期されるを指定してサービスを認証できます*identity*サービス。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="dc7a7-112">予想される ID とサービスから返される ID が一致しない場合、認証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="dc7a7-113">セキュリティ ネゴシエーションとタイムアウト</span><span class="sxs-lookup"><span data-stu-id="dc7a7-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="dc7a7-114"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> クラスの <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> プロパティの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="dc7a7-115">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="dc7a7-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="dc7a7-116">Windows 認証の使用時に発生する一般的な問題について重点的に説明します。</span><span class="sxs-lookup"><span data-stu-id="dc7a7-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dc7a7-117">参照</span><span class="sxs-lookup"><span data-stu-id="dc7a7-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="dc7a7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc7a7-118">Related Sections</span></span>  
 [<span data-ttu-id="dc7a7-119">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="dc7a7-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="dc7a7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc7a7-120">See Also</span></span>  
 [<span data-ttu-id="dc7a7-121">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="dc7a7-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="dc7a7-122">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="dc7a7-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
