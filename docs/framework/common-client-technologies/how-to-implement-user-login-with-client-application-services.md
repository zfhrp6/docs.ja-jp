---
title: "方法: クライアント アプリケーション サービスでユーザーのログインを実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9acd7e677b981c68b4aad7d10b41d7cef2e2eb06
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-user-login-with-client-application-services"></a>方法: クライアント アプリケーション サービスでユーザーのログインを実装する
クライアント アプリケーション サービスを使用して、既存の [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] プロファイル サービスを介してユーザーを検証できます。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] プロファイル サービスをセットアップする方法については、「[ASP.NET AJAX でのフォーム認証の使用](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)」を参照してください。  
  
 次の手順では、アプリケーションがクライアント認証サービス プロバイダーの 1 つを使用するように構成されている場合に、認証サービスを介してユーザーを検証する方法について説明します。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。  
  
 通常、検証はすべて `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> メソッドを介して実行します。 このメソッドは、認証サービスとの対話を構成済み認証プロバイダーを介して管理します。 詳細については、「[クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)」を参照してください。  
  
 フォーム認証手順では、実行中の [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 認証サービスへのアクセスが必要です。 クライアント アプリケーション サービス機能のエンド ツー エンド テストに関するガイダンスについては、「[チュートリアル: クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)」を参照してください。  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>メンバーシップ資格情報プロバイダーを使用して、フォーム認証でユーザーを認証するには  
  
1.  <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> インターフェイスを実装します。 <xref:System.Windows.Forms.Form?displayProperty=fullName> から派生したログイン ダイアログ ボックス クラスに対する <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=fullName> の実装コード例を次に示します。 このダイアログ ボックスには、ユーザー名とパスワードのテキスト ボックス、および "次回のために保存" チェック ボックスが含まれています。 クライアント認証プロバイダーが <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> メソッドを呼び出すと、フォームが表示されます。 ユーザーがログイン ダイアログ ボックスに情報を入力し [OK] をクリックすると、指定された値が新しい <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> オブジェクトに返されます。  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]  [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> メソッドを呼び出し、空の文字列をパラメーター値として渡します。 空の文字列を指定すると、このメソッドはアプリケーション用に構成された資格情報プロバイダーに対して <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> メソッドを内部的に呼び出します。 次のコード例では、このメソッドを呼び出して、Windows フォーム アプリケーション全体へのアクセスを制限しています。 このコードを <xref:System.Windows.Forms.Form.Load?displayProperty=fullName> ハンドラーに追加できます。  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]  [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>メンバーシップ資格情報プロバイダーを使用せずに、フォーム認証でユーザーを認証するには  
  
-   `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> メソッドを呼び出し、ユーザーから取得したユーザー名とパスワードの値を渡します。  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]  [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>Windows 認証でユーザーを認証するには  
  
-   `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> メソッドを呼び出し、空の文字列をパラメーターに渡します。 このメソッド呼び出しでは常に `true` が返され、Windows ID が含まれるユーザーのクッキー キャッシュにクッキーが追加されます。  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]  [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 このトピックのコード例は、Windows クライアント アプリケーションでの認証の最も単純な使用方法を示しています。 ただし、クライアント アプリケーション サービス、およびフォーム認証で `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> メソッドを呼び出すと、<xref:System.Net.WebException> がスローされる場合があります。 これは、認証サービスが使用できないことを示します。 この例外を処理する方法の例は、「[チュートリアル: クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [クライアント アプリケーション サービス](../../../docs/framework/common-client-technologies/client-application-services.md)   
 [クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)   
 [方法 : クライアント アプリケーション サービスを構成する](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)   
 [チュートリアル: クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)   
 [ASP.NET AJAX でのフォーム認証の使用](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)

