---
title: "WPF アプリケーションのリアルタイムなスタイラス入力を無効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fc4ec888419e385a57216f078387f731c0ab8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="43b46-102">WPF アプリケーションのリアルタイムなスタイラス入力を無効にする</span><span class="sxs-lookup"><span data-stu-id="43b46-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="43b46-103">Windows Presentation Foundation (WPF) Windows 7 タッチ入力を処理するためのサポートが組み込まれています。タブレットのプラットフォームのリアルタイムのスタイラス入力としてを介して渡されたサポート<xref:System.Windows.UIElement.OnStylusDown%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>、および<xref:System.Windows.UIElement.OnStylusMove%2A>イベント。</span><span class="sxs-lookup"><span data-stu-id="43b46-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="43b46-104">Windows 7 では、Win32 WM_TOUCH ウィンドウ メッセージとしてマルチタッチ入力も提供します。</span><span class="sxs-lookup"><span data-stu-id="43b46-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="43b46-105">これら 2 つの Api は、同じ HWND で相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="43b46-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="43b46-106">タッチを有効にするとは、タブレット プラットフォーム (WPF アプリケーションの既定値) を使用して無効に WM_TOUCH メッセージを入力します。</span><span class="sxs-lookup"><span data-stu-id="43b46-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="43b46-107">その結果、WM_TOUCH を使用して、メッセージを受信するタッチ WPF ウィンドウには、WPF での組み込みのスタイラス サポートを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43b46-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="43b46-108">これは、WM_TOUCH を使用するコンポーネントをホストする WPF ウィンドウなどのシナリオで適用します。</span><span class="sxs-lookup"><span data-stu-id="43b46-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="43b46-109">スタイラス入力をリッスンしている WPF を無効にするには、WPF ウィンドウによって追加された、タブレットのサポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="43b46-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b46-110">例</span><span class="sxs-lookup"><span data-stu-id="43b46-110">Example</span></span>  
 <span data-ttu-id="43b46-111">次のサンプル コードは、リフレクションを使用して既定のタブレット プラットフォームのサポートを削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43b46-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43b46-112">参照</span><span class="sxs-lookup"><span data-stu-id="43b46-112">See Also</span></span>  
 [<span data-ttu-id="43b46-113">スタイラスからの入力のインターセプト</span><span class="sxs-lookup"><span data-stu-id="43b46-113">Intercepting Input from the Stylus</span></span>](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
