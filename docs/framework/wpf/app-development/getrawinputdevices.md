---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5229eb7e72b63f3e44f67dc750d49acbf44410da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getrawinputdevices"></a><span data-ttu-id="2116d-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="2116d-102">GetRawInputDevices</span></span>
<span data-ttu-id="2116d-103">PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス (ヒューマン インターフェイス デバイス) を検出できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2116d-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2116d-104">構文</span><span class="sxs-lookup"><span data-stu-id="2116d-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2116d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2116d-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="2116d-106">[out]ポインター、 [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)を生の入力デバイスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="2116d-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2116d-107">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="2116d-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="2116d-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="2116d-108">HRESULT:</span></span>  
  
 <span data-ttu-id="2116d-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) S_OK が返される場合のみ PresentationHost.exe に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2116d-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="2116d-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2116d-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2116d-111">コメント</span><span class="sxs-lookup"><span data-stu-id="2116d-111">Remarks</span></span>  
 <span data-ttu-id="2116d-112">未加工入力デバイスは、キーボード、マウス、およびリモート コントロールのような比較的新しいデバイスを含む入力デバイスのセットです。</span><span class="sxs-lookup"><span data-stu-id="2116d-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="2116d-113">未加工の入力デバイスの一覧を取得すると、PresentationHost.exe は WM_INPUT 通知メッセージを受信するデバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="2116d-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2116d-114">参照</span><span class="sxs-lookup"><span data-stu-id="2116d-114">See Also</span></span>  
 [<span data-ttu-id="2116d-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span><span class="sxs-lookup"><span data-stu-id="2116d-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="2116d-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="2116d-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
