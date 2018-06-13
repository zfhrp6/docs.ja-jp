---
title: WPF アプリケーションのリアルタイムなスタイラス入力を無効にする
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: ddf4a7f4488f957b2f413d61ad02aa59beba30f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545663"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>WPF アプリケーションのリアルタイムなスタイラス入力を無効にする
Windows Presentation Foundation (WPF) Windows 7 タッチ入力を処理するためのサポートが組み込まれています。タブレットのプラットフォームのリアルタイムのスタイラス入力としてを介して渡されたサポート<xref:System.Windows.UIElement.OnStylusDown%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>、および<xref:System.Windows.UIElement.OnStylusMove%2A>イベント。 Windows 7 では、Win32 WM_TOUCH ウィンドウ メッセージとしてマルチタッチ入力も提供します。 これら 2 つの Api は、同じ HWND で相互に排他的です。 タッチを有効にするとは、タブレット プラットフォーム (WPF アプリケーションの既定値) を使用して無効に WM_TOUCH メッセージを入力します。 その結果、WM_TOUCH を使用して、メッセージを受信するタッチ WPF ウィンドウには、WPF での組み込みのスタイラス サポートを無効にする必要があります。 これは、WM_TOUCH を使用するコンポーネントをホストする WPF ウィンドウなどのシナリオで適用します。  
  
 スタイラス入力をリッスンしている WPF を無効にするには、WPF ウィンドウによって追加された、タブレットのサポートを削除します。  
  
## <a name="example"></a>例  
 次のサンプル コードは、リフレクションを使用して既定のタブレット プラットフォームのサポートを削除する方法を示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [スタイラスからの入力のインターセプト](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
