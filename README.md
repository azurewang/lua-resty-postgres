lua-resty-postgres
==================

Nonblocking Lua PostgreSQL driver library for ngx_lua

<h1>
<a name="synopsis" class="anchor" href="#synopsis"><span class="mini-icon mini-icon-link"></span></a>Synopsis</h1>

<pre>
local pg = require("resty.postgres")

local db = pg:new()
db:set_timeout(3000)

local ok, err = db:connect({host="127.0.0.1",port=5432, database="postgres",
                            user="admin",password="123456",compact=false})

if not ok then
    ngx.say(err)
end

local res, err = db:query("select id,name from test")
db:set_keepalive(0,100)

for i,v in ipairs(res) do
    ngx.say(string.format("%s\t%s",v.id,v.name))
end
</pre>


<h1>
<a name="author" class="anchor" href="#author"><span class="mini-icon mini-icon-link"></span></a>
Author
</h1>
<p>Azure Wang (王非)<a href="mailto:azure1st@gmail.com">azure1st@gmail.com</a></p>

<h1>
<a name="copyright-and-license" class="anchor" href="#copyright-and-license"><span class="mini-icon mini-icon-link"></span></a>
Copyright and License
</h1>
<p>This module is licensed under the BSD license.</p>

<p>Copyright (C) 2013, by Azure Wang (王非) <a href="mailto:azure1st@gmail.com">azure1st@gmail.com</a>.</p>

<p>All rights reserved.</p>

<p>Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:</p>

<ul>
	<li>
	<p>Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.</p>
</li>
<li>
	<p>Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.</p>
</li>
</ul>
<p>THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.</p>
