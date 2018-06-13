---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 51964358d27a16d9840e29be06c11f57de2fad23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548195"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="36458-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="36458-102">IWpfHostSupport</span></span>
<span data-ttu-id="36458-103">ホストするアプリケーション[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]PresentationHost.exe 経由のコンテンツは、ホストと PresentationHost.exe 間の統合ポイントを提供するには、このインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="36458-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36458-104">コメント</span><span class="sxs-lookup"><span data-stu-id="36458-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="36458-105"> Web ブラウザーなどのアプリケーションをホストできます[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]コンテンツを含む[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]XAML が失われるとします。</span><span class="sxs-lookup"><span data-stu-id="36458-105"> applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="36458-106">ホストに[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]コンテンツ、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]アプリケーションのインスタンスを作成する、 [WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=97911)です。</span><span class="sxs-lookup"><span data-stu-id="36458-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](http://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="36458-107">ホストされる[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]PresentationHost.exe、提供、ホスト型のインスタンスを作成[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]で表示するホストへのコンテンツ、 [WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=97911)です。</span><span class="sxs-lookup"><span data-stu-id="36458-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](http://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="36458-108">有効になっている統合`IWpfHostSupport`に PresentationHost.exe を許可。</span><span class="sxs-lookup"><span data-stu-id="36458-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
-   <span data-ttu-id="36458-109">検出し、ホスト アプリケーションが有用で生入力デバイス (ヒューマン インターフェイス デバイス) を登録します。</span><span class="sxs-lookup"><span data-stu-id="36458-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
-   <span data-ttu-id="36458-110">ホスト アプリケーションに登録済みの生の入力デバイスと適切なメッセージを転送からの入力メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="36458-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
-   <span data-ttu-id="36458-111">進行状況とエラーのカスタム ユーザー インターフェイスのホスト アプリケーションのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="36458-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36458-112">この API は、ローカル クライアント コンピューターでの使用のみを目的とし、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="36458-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="36458-113">メンバー</span><span class="sxs-lookup"><span data-stu-id="36458-113">Members</span></span>  
  
|<span data-ttu-id="36458-114">メンバー</span><span class="sxs-lookup"><span data-stu-id="36458-114">Member</span></span>|<span data-ttu-id="36458-115">説明</span><span class="sxs-lookup"><span data-stu-id="36458-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36458-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="36458-116">GetRawInputDevices</span></span>](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|<span data-ttu-id="36458-117">PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス (ヒューマン インターフェイス デバイス) を検出できるようにします。</span><span class="sxs-lookup"><span data-stu-id="36458-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="36458-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="36458-118">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|<span data-ttu-id="36458-119">E_NOTIMPL が返されない限り、メッセージを受信するたびに PresentationHost.exe によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="36458-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="36458-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="36458-120">GetCustomUI</span></span>](../../../../docs/framework/wpf/app-development/getcustomui.md)|<span data-ttu-id="36458-121">既定では、PresentationHost.exe は、独自の展開の進行状況と配置エラー WPF コンテンツが展開されているときに表示されるユーザー インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="36458-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
