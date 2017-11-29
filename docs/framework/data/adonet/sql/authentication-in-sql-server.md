---
title: "SQL Server での認証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3b597d04ee53a094d9c50dff406f57e5fd57b00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-sql-server"></a>SQL Server での認証
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] は、Windows 認証モードと混合モードという 2 つの認証モードをサポートしています。  
  
-   Windows 認証は既定の認証モードです。この [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] セキュリティ モデルは Windows と緊密に統合されているため、多くの場合、統合セキュリティと呼ばれます。 特定の Windows ユーザーおよび Windows グループが、信頼されたアカウントとして SQL Server へのログインが許可されます。 既に認証済みの Windows ユーザーは別途資格情報を提示する必要はありません。  
  
-   混合モードは、Windows による認証と [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] による認証の両方がサポートされます。 ユーザー名とパスワードの組み合わせは、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 内で管理されます。  
  
> [!IMPORTANT]
>  できるだけ Windows 認証を使用することをお勧めします。 Windows 認証では、暗号化された一連のメッセージを使用して [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のユーザーを認証します。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログインを使用した場合、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のログイン名とパスワードはネットワーク経由で渡されるためセキュリティが低下します。  
  
 Windows 認証では、既に Windows にログオンしているユーザーが別途 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] にログオンする必要はありません。 次の `SqlConnection.ConnectionString` では、Windows 認証が指定されているため、ユーザー名もパスワードも不要です。  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  ログインは、データベース ユーザーとは異なります。 ログインまたは Windows グループは、別個の操作でデータベース ユーザーまたはロールにマップする必要があります。 その後、ユーザーまたはロールに対してデータベース オブジェクトにアクセスするための権限を付与することになります。  
  
## <a name="authentication-scenarios"></a>認証のシナリオ  
 通常、以下の状況では Windows 認証が最良の選択肢です。  
  
-   ドメイン コントローラーが存在する。  
  
-   アプリケーションとデータベースが同じコンピューター上に存在する。  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express または LocalDB のインスタンスを使用している。  
  
 次の状況では、SQL Server ログインを使用することがよくあります。  
  
-   ワークグループが存在する。  
  
-   ユーザーが別の信頼されていないドメインから接続する。  
  
-   [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] などのインターネット アプリケーション。  
  
> [!NOTE]
>  Windows 認証を指定しても、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログインは無効になりません。 高い権限を持つ [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ログインを無効にするには、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ステートメント ALTER LOGIN DISABLE を使用します。  
  
## <a name="login-types"></a>ログインの種類  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、次の 3 種類のログインがサポートされています。  
  
-   ローカル Windows ユーザー アカウントまたは信頼されたドメイン アカウント。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] が Windows に依存する形で Windows ユーザー アカウントを認証します。  
  
-   Windows グループ。 Windows グループへのアクセス権を付与すると、そのグループに属しているすべての Windows ユーザー ログインにアクセス権が付与されます。  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログイン。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] はユーザー名およびパスワードのハッシュを master データベースに格納し、内部の認証方法を使ってログイン試行を検証します。  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、証明書または非対称キーから作成されたログインが提供されています。このログインはコード署名にのみ使用されます。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] への接続には使用できません。  
  
## <a name="mixed-mode-authentication"></a>混合モード認証  
 混合モード認証を使用する場合は、SQL Server に格納される [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログインを作成する必要があります。 さらに、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のユーザー名とパスワードを実行時に指定する必要があります。  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] は、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ("system administrator" の略) という名前の `sa` ログインが作成されます。 `sa` ログインには強力なパスワードを割り当て、アプリケーションで `sa` ログインを使用することは避けてください。 `sa` ログインは、サーバー全体に対する取り消し不可能な管理者の資格情報を持つ `sysadmin` 固定サーバー ロールにマップされます。 システム管理者のアクセス権が攻撃者によって取得された場合の潜在的な損害は計り知れません。 既定では、Windows `BUILTIN\Administrators` グループ (ローカル管理者のグループ) のすべてのメンバーが `sysadmin` ロールに所属しますが、sysadmin ロールから Windows の Administrators グループのメンバーを削除することもできます。  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 以降のバージョンで [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] を実行している場合、[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ログインに Windows のパスワード ポリシー メカニズムが適用されます。 パスワードの複雑性のポリシーは、考えられるパスワードの数を増やすことにより、総当たり攻撃を防ぐようにデザインされています。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] 内部で使用されるパスワードに、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] で使用されているものと同じ複雑性ポリシーおよび有効期限ポリシーを適用できます。  
  
> [!IMPORTANT]
>  ユーザー入力から文字列を連結することによって接続文字列を構築している場合、接続文字列のインジェクション攻撃に対して脆弱になります。 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> を使用すると、構文的に正しい接続文字列を実行時に作成できます。 詳細については、次を参照してください。[接続文字列ビルダー](../../../../../docs/framework/data/adonet/connection-string-builders.md)です。  
  
## <a name="external-resources"></a>外部リソース  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[プリンシパル](http://msdn.microsoft.com/library/bb543165.aspx)で[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]オンライン ブック|[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のログインおよびその他のセキュリティ プリンシパルについて説明します。|  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server におけるアプリケーション セキュリティ シナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [データ ソースへの接続](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [接続文字列](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
