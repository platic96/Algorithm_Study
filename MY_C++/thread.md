{
    shared_ptr&lt;thread&gt; <span class="brown2">thread</span>(<span class="purple">new</span> <span class="brown2">thread</span>([&amp;]() {
        <span class="green2">// 각 스레드의 메인 함수</span>
        <span class="green2">// 값을 가져올 수 있으면 루프를 돈다.</span>
        <span class="purple">while</span> (<span class="blue2">true</span>)
        {
            <span class="blue2">int</span> n;
            n = num;
            num++;

            <span class="purple">if</span> (n &gt;= MaxCount)
                <span class="purple">break</span>;

            <span class="purple">if</span> (<span class="brown2">IsPrimeNumber</span>(n))
            {
                primes.<span class="brown2">push_back</span>(n);
            }
        }
    }));
    <span class="green2">// 스레드 객체를 일단 갖고 있는다.</span>
    threads.<span class="brown2">push_back</span>(thread);
}

<span class="green2">// 모든 스레드가 일을 마칠 때까지 기다린다.</span>
<span class="purple">for</span> (<span class="blue2">auto</span> thread : threads)
{
    thread-&gt;<span class="brown2">join</span>();
}
<span class="green2">// 끝</span>

<span class="blue2">auto</span> t1 = <span class="brown2">chrono::system_clock::now</span>();

<span class="blue2">auto</span> duration = chrono::duration_cast&lt;chrono::milliseconds&gt;(t1 - t0).<span class="brown2">count</span>();
cout &lt;&lt; <span class="brown">"Took "</span> &lt;&lt; duration &lt;&lt; <span class="brown">" milliseconds."</span> &lt;&lt; endl;

<span class="green2">// PrintNumbers(primes);</span>

<span class="purple">return</span> <span class="green2">0</span>;