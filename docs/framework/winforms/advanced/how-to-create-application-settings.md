---
title: "方法 : アプリケーション設定を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アプリケーション設定, 作成"
  - "アプリケーション設定, Windows フォーム"
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : アプリケーション設定を作成する
マネージ コードを使用することにより、新しいアプリケーション設定を作成し、フォームまたはフォームのコントロールのプロパティにバインドして、これらの設定が実行時に自動的に読み込まれて保存されるようにすることができます。  
  
 次の手順では、<xref:System.Configuration.ApplicationSettingsBase> から派生するラッパー クラスを手動で作成します。  このクラスには、公開する各アプリケーション設定に対して、パブリックにアクセスできるプロパティを追加します。  
  
 また、Visual Studio デザイナーで最小限のコードを使用してこの手順を実行することもできます。  「[方法 : デザイナーを使用してアプリケーション設定を作成する](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\))」も参照してください。  
  
### 新しいアプリケーション設定をプログラムで作成するには  
  
1.  プロジェクトに新しいクラスを追加して、名前を変更します。  この手順では、このクラスを  `MyUserSettings` と呼びます。  クラスの派生元が <xref:System.Configuration.ApplicationSettingsBase> になるようクラス定義を変更します。  
  
2.  必要な各アプリケーション設定のこのラッパー クラスでプロパティを定義し、設定のスコープに応じて、そのプロパティを <xref:System.Configuration.ApplicationScopedSettingAttribute> または <xref:System.Configuration.UserScopedSettingAttribute> のいずれかを使用して適用します。  設定のスコープの詳細については、「[アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)」を参照してください。  ここまでで、コードは次のようになります。  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  アプリケーションでこのラッパー クラスのインスタンスを作成します。  これは、一般的にはメイン フォームのプライベート メンバーです。  クラスを定義したので、それをプロパティにバインドする必要があります。この場合は、フォームの <xref:System.Windows.Forms.Form.BackColor%2A> プロパティです。  これは、フォームの  `Load`  イベント ハンドラーで実行できます。  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  実行時に設定を変更する方法を提供する場合は、フォームを閉じるときにユーザーの現在の設定をディスクに保存する必要があります。そうしないと、これらの変更が失われます。  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     これで、新しいアプリケーション設定を正常に作成し、指定されたプロパティにバインドしました。  
  
## .NET Framework セキュリティ  
 既定の設定プロバイダーの <xref:System.Configuration.LocalFileSettingsProvider> は、情報をプレーン テキストとして構成ファイルに保存します。  これにより、セキュリティがオペレーティング システムが現在のユーザーに対して提供するファイル アクセスのセキュリティに制限されます。  このため、構成ファイルに保存される情報に注意する必要があります。  たとえば、アプリケーション設定の一般的な用途の 1 つとして、アプリケーションのデータ ストアをポイントする接続文字列を格納します。  ただし、セキュリティの問題があるため、このような文字列にパスワードは含まれません。  接続文字列の詳細については、「<xref:System.Configuration.SpecialSetting>」を参照してください。  
  
## 参照  
 <xref:System.Configuration.SpecialSettingAttribute>   
 <xref:System.Configuration.LocalFileSettingsProvider>   
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [方法 : アプリケーション設定を検証する](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)