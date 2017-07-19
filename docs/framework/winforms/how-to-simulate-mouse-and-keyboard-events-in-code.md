---
title: "方法 : マウス イベントとキーボード イベントをコードでシミュレートする | Microsoft Docs"
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
  - "キーボード, イベントのシミュレート"
  - "ユーザー入力, シミュレート"
  - "SendKeys, 使用"
  - "マウス クリック, シミュレート"
  - "マウス, イベントのシミュレート"
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : マウス イベントとキーボード イベントをコードでシミュレートする
Windows フォームは、プログラムでマウスおよびキーボード入力をシミュレートするためのいくつかのオプションを提供します。 ここでは、これらのオプションの概要について説明します。  
  
## マウス入力のシミュレート  
 マウス イベントをシミュレートする最善の方法は、`On`*EventName* メソッドを呼び出して、シミュレートの対象となるマウス イベントを発生させる方法です。 このオプションは、イベントを発生させるメソッドが保護され、コントロールまたはフォームの外部にアクセスできないため、通常はカスタム コントロールおよびフォーム内でのみ可能です。 たとえば、次の手順は、コードでマウスの右ボタンのクリックをシミュレートする方法を示しています。  
  
#### プログラムでマウスの右ボタンをクリックするには  
  
1.  <xref:System.Windows.Forms.MouseEventArgs.Button%2A> プロパティが <xref:System.Windows.Forms.MouseButtons?displayProperty=fullName> 値に設定された <xref:System.Windows.Forms.MouseEventArgs> を作成します。  
  
2.  この <xref:System.Windows.Forms.MouseEventArgs> を持つ <xref:System.Windows.Forms.Control.OnMouseClick%2A> メソッドを引数として呼び出します。  
  
 カスタム コントロールの詳細については、「[デザイン時の Windows フォーム コントロールの開発](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)」をご覧ください。  
  
 マウス入力をシミュレートする方法はほかにもあります。 たとえば、マウス入力によって標準的に設定する状態を表すコントロールのプロパティをプログラムで設定したり \(<xref:System.Windows.Forms.CheckBox> コントロールの <xref:System.Windows.Forms.CheckBox.Checked%2A> プロパティなど\)、シミュレートの対象イベントにアタッチされているデリゲートを直接呼び出したりできます。  
  
## キーボード入力のシミュレート  
 前述のマウス入力に関する戦略を使用することで、キーボード入力をシミュレートできますが、Windows フォームはアクティブなアプリケーションにキー入力を送信するための <xref:System.Windows.Forms.SendKeys> クラスも提供します。  
  
> [!CAUTION]
>  アプリケーションが国際対応し、さまざまなキーボードの使用を想定している場合は、<xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=fullName> の使用により予期しない結果になる可能性があるため、回避する必要があります。  
  
> [!NOTE]
>  .NET Framework 3.0 の <xref:System.Windows.Forms.SendKeys> クラスが更新され、Windows Vista で実行されるアプリケーションで使用できるようになりました。 Windows Vista の強化されたセキュリティ、\(ユーザー アカウント制御または UAC と呼ばれます\) により、前の実装は想定どおり機能できません。  
>   
>  <xref:System.Windows.Forms.SendKeys> クラスはタイミングの問題が発生する可能性があり、一部の開発者は回避策を取る必要がありました。 更新された実装は、引き続きタイミングの問題が発生する可能性がありますが、速度が少し向上し、回避策の変更が必要となる可能性があります。<xref:System.Windows.Forms.SendKeys> クラスは、最初に前の実装を使用しようとし、失敗した場合に、新しい実装を使用します。 その結果、<xref:System.Windows.Forms.SendKeys> クラスが別のオペレーティング システムと異なる動作を取る可能性があります。 さらに、<xref:System.Windows.Forms.SendKeys> クラスは、新しい実装を使用した場合、<xref:System.Windows.Forms.SendKeys.SendWait%2A> メソッドが別のプロセスに送信されたときにメッセージの処理を待機しません。  
>   
>  アプリケーションが、オペレーティング システムに関係なく一貫した動作に依存する場合、app.config ファイルに次のアプリケーション設定を追加することで、<xref:System.Windows.Forms.SendKeys> クラスが新しい実装を使用するよう強制することができます。  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  <xref:System.Windows.Forms.SendKeys> クラスが前の実装を使用するよう強制するには、代わりに値 `"JournalHook"` を使用します。  
  
#### 同じアプリケーションにキーストロークを送信するには  
  
1.  <xref:System.Windows.Forms.SendKeys> クラスの <xref:System.Windows.Forms.SendKeys.Send%2A> メソッドまたは <xref:System.Windows.Forms.SendKeys.SendWait%2A> メソッドを呼び出します。 指定されたキーストロークは、アプリケーションのアクティブなコントロールによって受信されます。 次のコード例では、<xref:System.Windows.Forms.SendKeys.Send%2A> を使用して、ユーザーがフォームのサーフェイスをダブルクリックしたときに、ENTER キーを押す操作をシミュレートします。 この例では、0 のタブ インデックスを持つ単一の <xref:System.Windows.Forms.Button> コントロールがある <xref:System.Windows.Forms.Form> を想定しています。  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### 別のアプリケーションにキーストロークを送信するには  
  
1.  キー入力を受信するアプリケーション ウィンドウをアクティブ化し、<xref:System.Windows.Forms.SendKeys.Send%2A> メソッドまたは <xref:System.Windows.Forms.SendKeys.SendWait%2A> メソッドを呼び出します。 別のアプリケーションをアクティブ化するマネージ メソッドがないため、ネイティブ Windows メソッドを使用して他のアプリケーションにフォーカスを設定する必要があります。 次のコード例は、プラットフォーム呼び出しを使用して `FindWindow` メソッドと `SetForegroundWindow` メソッドを呼び出し、電卓アプリケーションのウィンドウをアクティブ化してから、<xref:System.Windows.Forms.SendKeys.SendWait%2A> を呼び出して電卓アプリケーションに一連の計算を発行します。  
  
    > [!NOTE]
    >  電卓アプリケーションを特定する `FindWindow` 呼び出しの適切なパラメーターは、Windows のバージョンに応じて異なります。  次のコードでは、[!INCLUDE[win7](../../../includes/win7-md.md)] の電卓アプリケーションを検索します。[!INCLUDE[windowsver](../../../includes/windowsver-md.md)] では、最初のパラメーターを「SciCalc」に変更します。 Visual Studio に付属の Spy\+\+ ツールを使用して、適切なパラメーターを特定します。  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## 使用例  
 次のコード例は、前のコード例の完全なアプリケーションです。  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  また、「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 [Windows フォームでのユーザー入力](../../../docs/framework/winforms/user-input-in-windows-forms.md)