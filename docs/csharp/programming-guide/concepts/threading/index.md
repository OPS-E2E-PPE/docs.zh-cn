---
title: "线程处理 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 45ffa38254717c9aee29c3922bf801f6a90c716e
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="threading-c"></a><span data-ttu-id="7f6cd-102">线程处理 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-102">Threading (C#)</span></span>
<span data-ttu-id="7f6cd-103">通过线程处理，C# 程序可执行并行处理，让你可一次执行多个操作。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-103">Threading enables your C# program to perform concurrent processing so that you can do more than one operation at a time.</span></span> <span data-ttu-id="7f6cd-104">例如，可使用线程处理来监视来自用户的输入、执行后台任务和处理并行输入流。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-104">For example, you can use threading to monitor input from the user, perform background tasks, and handle simultaneous streams of input.</span></span>  
  
 <span data-ttu-id="7f6cd-105">线程具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="7f6cd-105">Threads have the following properties:</span></span>  
  
-   <span data-ttu-id="7f6cd-106">程序可利用线程执行并行处理。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-106">Threads enable your program to perform concurrent processing.</span></span>  
  
-   <span data-ttu-id="7f6cd-107">The .NET Framework <xref:System.Threading> 命名空间简化了线程的使用。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-107">The .NET Framework <xref:System.Threading> namespace makes using threads easier.</span></span>  
  
-   <span data-ttu-id="7f6cd-108">线程可共享应用程序的资源。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-108">Threads share the application's resources.</span></span> <span data-ttu-id="7f6cd-109">有关更多信息，请参见[使用线程和线程处理](https://msdn.microsoft.com/library/e1dx6b2h)。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-109">For more information, see [Using Threads and Threading](https://msdn.microsoft.com/library/e1dx6b2h).</span></span>  
  
 <span data-ttu-id="7f6cd-110">C# 程序默认具有一个线程。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-110">By default, a C# program has one thread.</span></span> <span data-ttu-id="7f6cd-111">但是，可创建辅助线程，将其用于与主线程并行执行代码。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-111">However, auxiliary threads can be created and used to execute code in parallel with the primary thread.</span></span> <span data-ttu-id="7f6cd-112">这些线程通常称为工作线程。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-112">These threads are often called *worker threads*.</span></span>  
  
 <span data-ttu-id="7f6cd-113">工作线程可用于执行耗时或时间关键型的任务，无需占用主线程。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-113">Worker threads can be used to perform time-consuming or time-critical tasks without tying up the primary thread.</span></span> <span data-ttu-id="7f6cd-114">例如，服务器应用程序中通常使用工作线程处理传入的请求，而不用等待上一个请求完成。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-114">For example, worker threads are often used in server applications to fulfill incoming requests without waiting for the previous request to be completed.</span></span> <span data-ttu-id="7f6cd-115">工作线程还用于在桌面应用程序中执行“后台”任务，让驱动用户界面元素的主线程仍然响应用户操作。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-115">Worker threads are also used to perform "background" tasks in desktop applications so that the main thread--which drives user interface elements--remains responsive to user actions.</span></span>  
  
 <span data-ttu-id="7f6cd-116">线程处理解决了吞吐量和响应性的问题，但也引入了死锁和争用条件等资源共享问题。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-116">Threading solves problems with throughput and responsiveness, but it can also introduce resource-sharing issues such as deadlocks and race conditions.</span></span> <span data-ttu-id="7f6cd-117">多线程特别适用于需要不同资源（如文件句柄和网络连接）的任务。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-117">Multiple threads are best for tasks that require different resources such as file handles and network connections.</span></span> <span data-ttu-id="7f6cd-118">向单个资源分配多线程可能会导致同步问题，而若在等待其他线程时造成线程频繁受阻，这与使用多线程的目的背道而驰。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-118">Assigning multiple threads to a single resource is likely to cause synchronization issues, and having threads frequently blocked when waiting for other threads defeats the purpose of using multiple threads.</span></span>  
  
 <span data-ttu-id="7f6cd-119">常见的策略是使用工作线程执行耗时或时间关键型的任务，这些任务不需要其他线程所用的很多资源。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-119">A common strategy is to use worker threads to perform time-consuming or time-critical tasks that do not require many of the resources used by other threads.</span></span> <span data-ttu-id="7f6cd-120">当然，程序中的某些资源必须由多个线程访问。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-120">Naturally, some resources in your program must be accessed by multiple threads.</span></span> <span data-ttu-id="7f6cd-121">对于这些情况，<xref:System.Threading> 命名空间提供了用于同步线程的类。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-121">For these cases, the <xref:System.Threading> namespace provides classes for synchronizing threads.</span></span> <span data-ttu-id="7f6cd-122">这些类包括 <xref:System.Threading.Mutex>、<xref:System.Threading.Monitor>、<xref:System.Threading.Interlocked>、<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-122">These classes include <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span>  
  
 <span data-ttu-id="7f6cd-123">可使用其中的部分或全部类进行多线程活动的同步，但对线程处理的某些支持受到 C# 语言的支持。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-123">You can use some or all these classes to synchronize the activities of multiple threads, but some support for threading is supported by the C# language.</span></span> <span data-ttu-id="7f6cd-124">例如，[Lock 语句](../../../../csharp/language-reference/keywords/lock-statement.md)通过隐式使用 <xref:System.Threading.Monitor> 提供同步功能。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-124">For example, the [Lock Statement](../../../../csharp/language-reference/keywords/lock-statement.md) provides synchronization features through implicit use of <xref:System.Threading.Monitor>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f6cd-125">自 [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)] 起，由于出现了 <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 类、[并行 LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688)、<xref:System.Collections.Concurrent?displayProperty=fullName> 命名空间中的新并发集合类，以及基于任务（而非线程）概念的新编程模型，多线程编程得到了大幅简化。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-125">Beginning with the [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> and <xref:System.Threading.Tasks.Task?displayProperty=fullName> classes, [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=fullName> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="7f6cd-126">有关详细信息，请参阅[并行编程](https://msdn.microsoft.com/library/dd460693)。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-126">For more information, see [Parallel Programming](https://msdn.microsoft.com/library/dd460693).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="7f6cd-127">相关主题</span><span class="sxs-lookup"><span data-stu-id="7f6cd-127">Related Topics</span></span>  
  
|<span data-ttu-id="7f6cd-128">标题</span><span class="sxs-lookup"><span data-stu-id="7f6cd-128">Title</span></span>|<span data-ttu-id="7f6cd-129">描述</span><span class="sxs-lookup"><span data-stu-id="7f6cd-129">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7f6cd-130">多线程应用程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-130">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|<span data-ttu-id="7f6cd-131">描述如何创建和使用线程。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-131">Describes how to create and use threads.</span></span>|  
|[<span data-ttu-id="7f6cd-132">多线程过程的参数和返回值 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-132">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|<span data-ttu-id="7f6cd-133">描述如何使用多线程的应用程序传递和返回参数。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-133">Describes how to pass and return parameters with multithreaded applications.</span></span>|  
|[<span data-ttu-id="7f6cd-134">演练：利用 BackgroundWorker 组件进行多线程处理 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-134">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|<span data-ttu-id="7f6cd-135">演示如何创建简单的多线程应用程序。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-135">Shows how to create a simple multithreaded application.</span></span>|  
|[<span data-ttu-id="7f6cd-136">线程同步 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-136">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|<span data-ttu-id="7f6cd-137">描述如何控制线程的交互。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-137">Describes how to control the interactions of threads.</span></span>|  
|[<span data-ttu-id="7f6cd-138">线程计时器 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-138">Thread Timers (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|<span data-ttu-id="7f6cd-139">描述如何按固定时间间隔在单独的线程上运行过程。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-139">Describes how to run procedures on separate threads at fixed intervals.</span></span>|  
|[<span data-ttu-id="7f6cd-140">线程池 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-140">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|<span data-ttu-id="7f6cd-141">描述如何使用由系统托管的工作线程池。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-141">Describes how to use a pool of worker threads that are managed by the system.</span></span>|  
|[<span data-ttu-id="7f6cd-142">如何：使用线程池 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-142">How to: Use a Thread Pool (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|<span data-ttu-id="7f6cd-143">展示线程池中多线程的同步使用。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-143">Demonstrates synchronized use of multiple threads in the thread pool.</span></span>|  
|[<span data-ttu-id="7f6cd-144">线程处理</span><span class="sxs-lookup"><span data-stu-id="7f6cd-144">Threading</span></span>](https://msdn.microsoft.com/library/3e8s7xdd)|<span data-ttu-id="7f6cd-145">描述如何在 .NET Framework 中实现线程处理。</span><span class="sxs-lookup"><span data-stu-id="7f6cd-145">Describes how to implement threading in the .NET Framework.</span></span>|
