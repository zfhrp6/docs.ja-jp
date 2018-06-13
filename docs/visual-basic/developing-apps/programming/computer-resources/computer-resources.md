---
title: コンピューター リソースへのアクセス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 7128a71f28d1755a14fcda5f09bee11202ab4154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586245"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="09145-102">コンピューター リソースへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09145-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="09145-103">`My.Computer` オブジェクトは、`My` の中心となる 3 つのオブジェクトの 1 つであり、情報とよく使用される機能へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="09145-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="09145-104">`My.Computer` には、アプリケーションが実行されているコンピューターにアクセスするためのメソッド、プロパティ、イベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="09145-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="09145-105">そのオブジェクトには、以下のものがあります。</span><span class="sxs-lookup"><span data-stu-id="09145-105">Its objects include:</span></span>  
  
-   <xref:Microsoft.VisualBasic.Devices.Audio>
-   <span data-ttu-id="09145-106">クリップボード (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="09145-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
-   <xref:Microsoft.VisualBasic.Devices.Clock>
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem>
-   <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
-   <xref:Microsoft.VisualBasic.Devices.Keyboard>
-   <xref:Microsoft.VisualBasic.Devices.Mouse>
-   <xref:Microsoft.VisualBasic.Devices.Network>
-   <xref:Microsoft.VisualBasic.Devices.Ports>
-   <span data-ttu-id="09145-107">レジストリ (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="09145-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="09145-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="09145-108">In this section</span></span>

<span data-ttu-id="09145-109">[サウンドの再生](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span><span class="sxs-lookup"><span data-stu-id="09145-109">[Playing Sounds](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span></span>  
<span data-ttu-id="09145-110">`My.Computer.Audio` に関連付けられたタスクを一覧表示します (例: バックグラウンドでのサウンドの再生)。</span><span class="sxs-lookup"><span data-stu-id="09145-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

<span data-ttu-id="09145-111">[クリップボードのデータの格納と読み取り](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span><span class="sxs-lookup"><span data-stu-id="09145-111">[Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span></span>  
<span data-ttu-id="09145-112">`My.Computer.Clipboard` に関連付けられたタスクを一覧表示します (例: クリップボードからのデータ読み取り、またはクリップボードへのデータ書き込み)。</span><span class="sxs-lookup"><span data-stu-id="09145-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

<span data-ttu-id="09145-113">[コンピューターについての情報の取得](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span><span class="sxs-lookup"><span data-stu-id="09145-113">[Getting Information about the Computer](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span></span>  
<span data-ttu-id="09145-114">`My.Computer.Info` に関連付けられたタスクを一覧表示します (例: コンピューターの完全な名前または IP アドレスの特定)。</span><span class="sxs-lookup"><span data-stu-id="09145-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

<span data-ttu-id="09145-115">[キーボードへのアクセス](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="09145-115">[Accessing the Keyboard](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span></span>  
<span data-ttu-id="09145-116">`My.Computer.Keyboard` に関連付けられたタスクを一覧表示します (例: CapsLock がオンになっているかどうかの特定)。</span><span class="sxs-lookup"><span data-stu-id="09145-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

<span data-ttu-id="09145-117">[マウスへのアクセス](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span><span class="sxs-lookup"><span data-stu-id="09145-117">[Accessing the Mouse](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span></span>  
<span data-ttu-id="09145-118">`My.Computer.Mouse` に関連付けられたタスクを一覧表示します (例: マウスの有無の特定)。</span><span class="sxs-lookup"><span data-stu-id="09145-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

<span data-ttu-id="09145-119">[ネットワーク操作の実行](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span><span class="sxs-lookup"><span data-stu-id="09145-119">[Performing Network Operations](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span></span>  
<span data-ttu-id="09145-120">`My.Computer.Network` に関連付けられたタスクを一覧表示します (例: ファイルのアップロードまたはダウンロード)。</span><span class="sxs-lookup"><span data-stu-id="09145-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

<span data-ttu-id="09145-121">[コンピューターのポートへのアクセス](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span><span class="sxs-lookup"><span data-stu-id="09145-121">[Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span></span>  
<span data-ttu-id="09145-122">`My.Computer.Ports` に関連付けられたタスクを一覧表示します (例: 使用できるシリアル ポートの表示、またはシリアル ポートへの文字列の送信)。</span><span class="sxs-lookup"><span data-stu-id="09145-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

<span data-ttu-id="09145-123">[レジストリからの読み取りとレジストリへの書き込み](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="09145-123">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
<span data-ttu-id="09145-124">`My.Computer.Registry` に関連付けられたタスクを一覧表示します (例: レジストリ キーからのデータ読み取り、またはレジストリ キーへのデータ書き込み)。</span><span class="sxs-lookup"><span data-stu-id="09145-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
