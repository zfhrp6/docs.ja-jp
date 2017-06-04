---
title: "Windows フォームのセキュリティに関するその他の考慮事項 | Microsoft Docs"
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
  - "API 呼び出し, Windows フォームのセキュリティ設定"
  - "API, 呼び出し"
  - "クリップボードのトピック, セキュリティ (アクセスの)"
  - "セキュリティ [Windows フォーム]"
  - "セキュリティ [Windows フォーム], 呼び出し (API の)"
  - "Windows API, 呼び出し"
  - "Windows API, 安全な呼び出し"
  - "Windows API, Windows フォームのセキュリティ設定"
  - "Windows フォーム, 安全な呼び出し (Windows API の)"
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Windows フォームのセキュリティに関するその他の考慮事項
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] セキュリティ設定によっては、ローカル コンピューターとは異なり、アプリケーションが部分信頼環境で実行されることがあります。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、ファイル システム、ネットワーク、アンマネージ API などの重要なローカル リソースへのアクセスを他のリソースの場合よりも制限します。  セキュリティ設定により、セキュリティ システムが検証できない Microsoft Win32 API やその他の API を呼び出す機能が影響を受けます。  また、ファイルやデータへのアクセス、印刷など、アプリケーションのその他の処理にも影響があります。  部分信頼環境でのファイルやデータへのアクセスの詳細については、「[Windows フォームにおけるファイルおよびデータへのより安全なアクセス](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)」を参照してください。  部分信頼環境での印刷の詳細については、「[Windows フォームでのより安全な印刷](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)」を参照してください。  
  
 以下のセクションでは、クリップボードの使用、ウィンドウ操作の実行、および部分信頼環境で動作しているアプリケーションからの Win32 API の呼び出しについて説明しています。  
  
## クリップボードへのアクセス  
 <xref:System.Security.Permissions.UIPermission> クラスがクリップボードへのアクセスを制御し、関連付けられた <xref:System.Security.Permissions.UIPermissionClipboard> 列挙値がアクセスのレベルを示します。  使用されるアクセス許可レベルを次の表に示します。  
  
|UIPermissionClipboard の値|Description|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|クリップボードは制限なしに使用できます。|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|クリップボードは制限付きで使用できます。  クリップボードにデータを格納する機能 \(\[コピー\] または \[切り取り\] のコマンド操作\) は制限されません。  テキスト ボックスなど、\[貼り付け\] を受け入れる固有のコントロールは、クリップボードのデータを受け入れます。しかし、ユーザー コントロールはプログラムでクリップボードからデータを読み取ることができません。|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|クリップボードは使用できません。|  
  
 既定では、\[イントラネット\] ゾーンでは <xref:System.Security.Permissions.UIPermissionClipboard> アクセスが許可され、\[インターネット\] ゾーンでは <xref:System.Security.Permissions.UIPermissionClipboard> アクセスが許可されます。  つまり、アプリケーションはクリップボードにデータをコピーできますが、プログラムでクリップボードに貼り付けたりクリップボードから読み取ったりはできません。  これらの制限により、完全に信頼されていないプログラムは、他のアプリケーションによってクリップボードにコピーされた内容を読み取ることができません。  アプリケーションがクリップボードへの完全なアクセスを必要とするにもかかわらず、アクセス許可がない場合は、アプリケーションに対するアクセス許可の度合いを高める必要があります。  アクセス許可を増やす方法の詳細については、「[コード アクセス セキュリティと ADO.NET](http://msdn.microsoft.com/ja-jp/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)」を参照してください。  
  
## ウィンドウ操作  
 <xref:System.Security.Permissions.UIPermission> クラスは、ウィンドウ操作や他の UI 関連処理を実行するアクセス許可も管理し、関連付けられた <xref:System.Security.Permissions.UIPermissionWindow> 列挙値がアクセスのレベルを示します。  使用されるアクセス許可レベルを次の表に示します。  
  
 既定では、\[イントラネット\] ゾーンでは <xref:System.Security.Permissions.UIPermissionWindow> アクセスが許可され、\[インターネット\] ゾーンでは <xref:System.Security.Permissions.UIPermissionWindow> アクセスが許可されます。  つまり、\[インターネット\] ゾーンでは、アプリケーションがほとんどのウィンドウ操作および UI 関連処理を実行できますが、ウィンドウの外観が変更されます。  変更されたウィンドウには、最初の実行時にバルーン通知が表示され、変更されたタイトル バー テキストが表示され、タイトル バーに閉じるボタンが必要になります。  バルーン通知とタイトル バーは、アプリケーションのユーザーに、アプリケーションが部分信頼で動作していることを示します。  
  
|UIPermissionWindow の値|Description|  
|---------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow>|ユーザーは、すべてのウィンドウとユーザー入力イベントを無制限に使用できます。|  
|<xref:System.Security.Permissions.UIPermissionWindow>|ユーザーは、セーフ トップレベル ウィンドウとセーフ サブウィンドウだけを描画に使用でき、それらのセーフ トップレベル ウィンドウとセーフ サブウィンドウの中のユーザー インターフェイスに対するユーザー入力イベントだけを使用できます。  これらのセーフ ウィンドウには明確なラベルが付けられ、最小サイズと最大サイズに制限があります。  これらの制限により、システム ログオン画面やシステム デスクトップの偽装など、有害の可能性がある、なりすまし攻撃が防止されます。また、親ウィンドウ、フォーカス関連の API、および <xref:System.Windows.Forms.ToolTip> コントロールの使用に対して、プログラムによるアクセスが制限されます。|  
|<xref:System.Security.Permissions.UIPermissionWindow>|ユーザーは、セーフ サブウィンドウだけを描画に使用でき、そのセーフ サブウィンドウの中のユーザー インターフェイスに対するユーザー入力イベントだけを使用できます。  ブラウザー内に表示されるコントロールは、セーフ サブウィンドウの一例です。|  
|<xref:System.Security.Permissions.UIPermissionWindow>|ユーザーは、ウィンドウおよびユーザー インターフェイス イベントを使用できません。  ユーザー インターフェイスは使用できません。|  
  
 <xref:System.Security.Permissions.UIPermissionWindow> 列挙値によって示される各アクセス許可レベルでは、レベルが下がるにつれて許可される処理が少なくなります。  <xref:System.Security.Permissions.UIPermissionWindow> と <xref:System.Security.Permissions.UIPermissionWindow> の値によって制限される処理を次の表に示します。  各メンバーに対して必要なアクセス許可については、.NET Framework クラス ライブラリのドキュメントで該当するメンバーのトピックを参照してください。  
  
 <xref:System.Security.Permissions.UIPermissionWindow> アクセス許可は、次の表に示される処理を制限します。  
  
|コンポーネント|制限される処理|  
|-------------|-------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> プロパティの設定|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.Parent%2A> プロパティの取得<br />-   `Region` プロパティの設定<br />-   <xref:System.Windows.Forms.Control.FindForm%2A>、<xref:System.Windows.Forms.Control.Focus%2A>、<xref:System.Windows.Forms.Control.FromChildHandle%2A>、<xref:System.Windows.Forms.Control.FromHandle%2A>、<xref:System.Windows.Forms.Control.PreProcessMessage%2A>、<xref:System.Windows.Forms.Control.ReflectMessage%2A>、または <xref:System.Windows.Forms.Control.SetTopLevel%2A> の各メソッドの呼び出し<br />-   返されたコントロールが呼び出し元のコントロールの子でない場合には、<xref:System.Windows.Forms.Control.GetChildAtPoint%2A> メソッドの呼び出し<br />-   コンテナー コントロール内でのコントロール フォーカスの変更|  
|<xref:System.Windows.Forms.Cursor>|-   <xref:System.Windows.Forms.Cursor.Clip%2A> プロパティの設定<br />-   <xref:System.Windows.Forms.Control.Hide%2A> メソッドの呼び出し|  
|<xref:System.Windows.Forms.DataGrid>|-   <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> メソッドの呼び出し|  
|<xref:System.Windows.Forms.Form>|-   <xref:System.Windows.Forms.Form.ActiveForm%2A> プロパティまたは <xref:System.Windows.Forms.Form.MdiParent%2A> プロパティの取得<br />-   <xref:System.Windows.Forms.Form.ControlBox%2A>、<xref:System.Windows.Forms.Form.ShowInTaskbar%2A> プロパティ、または <xref:System.Windows.Forms.Form.TopMost%2A> プロパティの設定<br />-   50% より小さい <xref:System.Windows.Forms.Form.Opacity%2A> プロパティ値の設定<br />-   プログラムで <xref:System.Windows.Forms.Form.WindowState%2A> プロパティを <xref:System.Windows.Forms.FormWindowState> に設定<br />-   <xref:System.Windows.Forms.Form.Activate%2A> メソッドの呼び出し<br />-   <xref:System.Windows.Forms.FormBorderStyle>、<xref:System.Windows.Forms.FormBorderStyle>、および <xref:System.Windows.Forms.FormBorderStyle> という <xref:System.Windows.Forms.FormBorderStyle> 列挙値の使用|  
|<xref:System.Windows.Forms.NotifyIcon>|-   <xref:System.Windows.Forms.NotifyIcon> コンポーネントの使用は完全に制限されます。|  
  
 <xref:System.Security.Permissions.UIPermissionWindow> の値は、<xref:System.Security.Permissions.UIPermissionWindow> の値による制限に加えて、次の表に示される処理を制限します。  
  
|コンポーネント|制限される処理|  
|-------------|-------------|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog> クラスから派生したダイアログ ボックスの表示|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateGraphics%2A> メソッドの呼び出し<br />-   <xref:System.Windows.Forms.Control.Cursor%2A> プロパティの設定|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   <xref:System.Windows.Forms.Cursor.Current%2A> プロパティの設定|  
|<xref:System.Windows.Forms.MessageBox>|-   <xref:System.Windows.Forms.Form.Show%2A> メソッドの呼び出し|  
  
### サードパーティ コントロールのホスト  
 フォームでサードパーティ コントロールをホストしている場合、他の種類のウィンドウ操作が発生する可能性があります。  サードパーティ コントロールとは、自分で開発およびコンパイルを行っていないカスタムの <xref:System.Windows.Forms.UserControl> です。  ホスト シナリオを攻略するのは困難ですが、理論上、サードパーティ コントロールが描画サーフェイスを拡張して、フォームの領域全体を対象にする可能性があります。  このようなコントロールは、重要なダイアログ ボックスを模倣し、ユーザーのユーザー名\/パスワードの組み合わせや銀行口座番号などの情報を要求する可能性があります。  
  
 このような考えられるリスクを制限するために、信頼できる販売元のサードパーティ コントロールのみを使用します。  確認できないソースからサードパーティ コントロールをダウンロードした場合、攻略行為が実行されないかソース コードを確認します。  ソースに悪意がないことを検証してから、アセンブリを自分でコンパイルし、ソースがアセンブリと一致することを確認します。  
  
## Win32 API 呼び出し  
 アプリケーションのデザインで Win32 API から関数を呼び出す必要がある場合は、アンマネージ コードにアクセスします。  この場合、Win32 API の呼び出しまたは値を使用するときに、ウィンドウまたはオペレーティング システムに対するコードの動作が決定できません。  <xref:System.Security.Permissions.SecurityPermission> クラスと、<xref:System.Security.Permissions.SecurityPermissionFlag> 列挙定数の <xref:System.Security.Permissions.SecurityPermissionFlag> 値によって、アンマネージ コードへのアクセスを制御します。  アプリケーションは、<xref:System.Security.Permissions.SecurityPermissionFlag> アクセス許可が与えられている場合にだけ、アンマネージ コードにアクセスできます。  既定では、ローカルに動作しているアプリケーションだけがアンマネージ コードを呼び出すことができます。  
  
 Windows フォームのいくつかのメンバーが、<xref:System.Security.Permissions.SecurityPermissionFlag> アクセス許可を必要とするアンマネージ アクセスを提供します。  アクセス許可を必要とする <xref:System.Windows.Forms> 名前空間のメンバーを次の表に示します。  メンバーに対して必要なアクセス許可の詳細については、.NET Framework クラス ライブラリのドキュメントを参照してください。  
  
|コンポーネント|メンバー|  
|-------------|----------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッド<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> プロパティ<br />-   `Exit` メソッド<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> メソッド<br />-   <xref:System.Windows.Forms.Application.ThreadException> イベント|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> メソッド<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A> メソッド<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> メソッド<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> メソッド|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> メソッド<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> メソッド<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> メソッド<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> メソッド|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A>メソッド<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> メソッド|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> クラス|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> メソッド|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> メソッド<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> メソッド|  
  
 アプリケーションがアンマネージ コードを呼び出すアクセス許可を持っていない場合、<xref:System.Security.Permissions.SecurityPermissionFlag> アクセス許可を要求するか、別の方法で機能を実装することを考慮する必要があります。多くの場合、Windows フォームでは代わりに Win32 API 関数のマネージ コードを提供します。  代わりの手段がなく、アプリケーションがアンマネージ コードにアクセスする必要がある場合は、アプリケーションに対するアクセス許可を増やす必要があります。  
  
 アンマネージ コードを呼び出すアクセス許可を与えられたアプリケーションは、ほとんど何でも実行できます。  そのため、アンマネージ コードを呼び出すアクセス許可は、信頼されたソースからのアプリケーションに対してだけ与えるようにしてください。  また、アプリケーションによっては、アンマネージ コードへの呼び出しを生成するアプリケーション機能の一部をオプションにするか、完全信頼環境でのみ有効にすることもできます。  危険なアクセス許可の詳細については、「[危険なアクセス許可とポリシー管理](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)」を参照してください。  アクセス許可の昇格の詳細については、「[NIB: General Security Policy Administration](http://msdn.microsoft.com/ja-jp/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)」を参照してください。  
  
## 参照  
 [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)   
 [Windows フォームでのより安全な印刷](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)   
 [Windows フォームのセキュリティの概要](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Windows フォームのセキュリティ](../../../docs/framework/winforms/windows-forms-security.md)   
 [ClickOnce アプリケーションのセキュリティ](../Topic/Securing%20ClickOnce%20Applications.md)