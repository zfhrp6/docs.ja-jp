---
title: "軽減策: CspParameters.ParentWindowHandle で HWND を受け取る | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 84aadd0ccd7b5c786612d06ca0b46fb5aecd3d2b
ms.openlocfilehash: d068da3253056712f0aab7d536d8faf7c836422b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a>軽減策: CspParameters.ParentWindowHandle で HWND を受け取る

.NET Framework 2.0 で導入された <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティをアプリケーションに使用すると、親ウィンドウのハンドル値を登録できます。これを利用して、キーにアクセスする必要がある UI (PIN プロンプトや同意を求めるダイアログなど) を、指定したウィンドウの子のモーダルとして開くことができます。 .NET Framework 4.7 以降をターゲットとするアプリケーションでは、ウィンドウ ハンドル (HWND) をこのプロパティに割り当てることができます。

.NET Framework 4.6.2 までの .NET Framework バージョンでは、<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティに割り当てられている値は、HWND 値があるメモリ内の場所を表す <xref:System.IntPtr> であると想定されています。 Windows 7 以前のバージョンの Windows オペレーティング システムでは、このプロパティを `form.Handle` に設定しても影響がありませんが、Windows 8 以降のバージョンでは、<xref:System.Security.Cryptography> の結果として "パラメーターが正しくありません" というエラーが表示されます。

.NET Framework 4.7 を対象とするアプリ以降では、Windows フォーム アプリケーションは、次のようなコードを使用して、<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティを設定できます。

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a>影響

親ウィンドウの関係を登録する .NET Framework 4.7 以降をターゲットとするアプリケーションの場合、次のように単純な形式を使用することをお勧めします。

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a>軽減策

正しい値が `form.Handle` 値を保持するメモリ位置のアドレスであると特定した場合、次のように <xref:System.AppContext> スイッチ `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` を `true` に変更することでこの動作の変更を解除することができます。

- プログラムで、<xref:System.AppContext> インスタンスの互換性スイッチを設定する

- app.config ファイルの `<runtime>` セクションに以下の行を追加する:
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

逆に、.NET Framework 4.7 で実行するアプリケーションには新しい動作を選択し、旧バージョンの .NET Framework バージョンをターゲットとする場合は、<xref:System.AppContext> スイッチを `false` に設定できます。
 
## <a name="see-also"></a>関連項目

[.NET Framework 4.7 における再ターゲットの変更点](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

