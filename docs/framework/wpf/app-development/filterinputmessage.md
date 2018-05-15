---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 69bc1e973b690454bcf91487c12dc4ce0ac46a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="filterinputmessage"></a><span data-ttu-id="af7d1-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="af7d1-102">FilterInputMessage</span></span>
<span data-ttu-id="af7d1-103">E_NOTIMPL が返されない限り、メッセージを受信するたびに PresentationHost.exe によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="af7d1-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af7d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="af7d1-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af7d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af7d1-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="af7d1-106">[in] 未加工入力を取得するウィンドウに送信される WM_INPUT メッセージ。</span><span class="sxs-lookup"><span data-stu-id="af7d1-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="af7d1-107">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="af7d1-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="af7d1-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="af7d1-108">HRESULT:</span></span>  
  
 <span data-ttu-id="af7d1-109">S_OK - フィルターはメッセージを処理せず、それ以降の処理は実行されることがあります。</span><span class="sxs-lookup"><span data-stu-id="af7d1-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="af7d1-110">S_FALSE - フィルターはこのメッセージを処理しました。それ以降の処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="af7d1-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="af7d1-111">E_NOTIMPL – この値が返される場合は[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)は再度呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="af7d1-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="af7d1-112">この値は、カスタムの進行状況の提供のみを対象とするホスト アプリケーションから返されることがあります。PresentationHost.exe へのエラー ユーザー インターフェイスは、PresentationHost.exe からの未加工の入力メッセージの転送を対象としていません。</span><span class="sxs-lookup"><span data-stu-id="af7d1-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af7d1-113">コメント</span><span class="sxs-lookup"><span data-stu-id="af7d1-113">Remarks</span></span>  
 <span data-ttu-id="af7d1-114">PresentationHost.exe は、キーボード、マウス、およびリモート コントロールなどのさまざまな未加工入力デバイスのターゲットになります。</span><span class="sxs-lookup"><span data-stu-id="af7d1-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="af7d1-115">場合によって、ホスト アプリケーションでの動作は PresentationHost.exe で使用される入力に依存します。</span><span class="sxs-lookup"><span data-stu-id="af7d1-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="af7d1-116">たとえば、ホスト アプリケーションは、特定のユーザー インターフェイス要素を表示するかどうかを判断するために、特定の入力メッセージの受信に依存することがあります。</span><span class="sxs-lookup"><span data-stu-id="af7d1-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="af7d1-117">ホスト アプリケーションがこれらの動作を提供するために必要な入力メッセージを受信するには、PresentationHost.exe では、呼び出すことによって、ホストされるアプリケーションに適切な未加工の入力メッセージを転送[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7d1-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="af7d1-118">ホストされるアプリケーションでは、生の入力メッセージを受信によって返された生の入力デバイス (ヒューマン インターフェイス デバイス) のセットを登録して[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)です。</span><span class="sxs-lookup"><span data-stu-id="af7d1-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7d1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="af7d1-119">See Also</span></span>  
 [<span data-ttu-id="af7d1-120">WM_INPUT 通知</span><span class="sxs-lookup"><span data-stu-id="af7d1-120">WM_INPUT Notification</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
