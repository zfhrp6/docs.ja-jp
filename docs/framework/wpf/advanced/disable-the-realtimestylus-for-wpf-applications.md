---
title: "WPF アプリケーションのリアルタイムなスタイラス入力を無効にする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# WPF アプリケーションのリアルタイムなスタイラス入力を無効にする
Windows Presentation Foundation \(WPF\) には Windows 7 のタッチ入力処理をサポートする機能が組み込まれています。スタイラス入力を <xref:System.Windows.UIElement.OnStylusDown%2A> イベント、<xref:System.Windows.UIElement.OnStylusUp%2A> イベントおよび <xref:System.Windows.UIElement.OnStylusMove%2A> イベントとして、タブレットからリアルタイムに実行できるようにします。  また、Windows 7 ではマルチタッチ入力による Win32 WM\_TOUCH ウィンドウ メッセージにも対応しています。  これらの 2 つの API を、同じ HWND で同時に使用することはできません。  タブレットからのタッチ入力を有効にすると \(WPF アプリケーションの既定\)、WM\_TOUCH messages は無効になります。  そのため、WM\_TOUCH を使用して WPF ウィンドウからタッチ メッセージを受信する場合には、WPF に組み込まれているスタイラス入力のサポートを無効にする必要があります。  この状況に該当するのは、WM\_TOUCH を使用するコンポーネントをホストしている WPF ウィンドウなどです。  
  
 WPF でのスタイラス入力の待機を無効にするには、WPF ウィンドウで追加されたタブレットのサポートをすべて削除します。  
  
## 使用例  
 次に示すサンプル コードでは、リフレクションを使って既定のタブレット入力のサポートを削除する方法を示しています。  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## 参照  
 [スタイラスからの入力のインターセプト](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)