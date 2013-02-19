lua-resty-postgres
==================

Nonblocking Lua PostgreSQL driver library for ngx_lua

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
