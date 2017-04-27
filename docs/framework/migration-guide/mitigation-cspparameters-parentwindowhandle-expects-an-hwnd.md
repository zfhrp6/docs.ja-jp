---
title: "軽減策: CspParameters.ParentWindowHandle で HWND を受け取る | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- CspParameters.ParentWindowHandle
- CspParameters.ParentWindowHandle retargeting change
ms.assetid: 33264333-71d6-4d43-8827-9c98878cfea7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: 22c258b06a5cc8fa3fec72665d7e413b0cdd11ee
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a>軽減策: CspParameters.ParentWindowHandle で HWND を受け取る

.NET Framework 2.0 で導入された <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティをアプリケーションに使用すると、親ウィンドウのハンドル値を登録できます。これを利用して、キーにアクセスする必要がある UI (PIN プロンプトや同意を求めるダイアログなど) を、指定したウィンドウの子のモーダルとして開くことができます。 .NET Framework 4.7 以降をターゲットとするアプリケーションでは、ウィンドウ ハンドル (HWND) をこのプロパティに割り当てることができます。

.NET Framework 4.6.2 までの .NET Framework バージョンでは、<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティに割り当てられている値は、HWND 値があるメモリ内の場所を表す <xref:System.IntPtr> であると想定されています。 Windows 7 以前のバージョンの Windows オペレーティング システムでは、このプロパティを `form.Handle` に設定しても影響がありませんが、Windows 8 以降のバージョンでは、<xref:System.Security.Cryptography> の結果として "パラメーターが正しくありません" エラーが表示されます。

.NET Framework 4.7 以降をターゲットとするアプリの場合、Windows フォーム アプリケーションでは次のようなコードで <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティを設定できます。

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a>影響

親ウィンドウの関係を登録する .NET Framework 4.7 以降をターゲットとするアプリケーションの場合、次のように単純な形式を使用することをお勧めします。

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a>軽減策

正しい値が `form.Handle` 値を保持するメモリ位置のアドレスであると特定した場合、次のように <xref:System.Security.AppContext> スイッチ `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` を `true` に変更することでこの動作の変更を解除することができます。

- プログラムで、[AppContext](assetID:///T:System.Security.AppContext) インスタンスの互換性スイッチを設定する

- app.config ファイルの `<runtime>` セクションに以下の行を追加する。
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

逆に、.NET Framework 4.7 で実行するアプリケーションには新しい動作を選択し、旧バージョンの .NET Framework バージョンをターゲットとする場合は、<xref:System.Security.AppContext> スイッチを `false` に設定できます。
 
## <a name="see-also"></a>関連項目

[.NET Framework 4.7 における再ターゲットの変更点](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

