media
=====
 
 
	 function Stream:receive(data)
	+  -- Handle data
   self:emit("data", data)
-  local lines = split(data, "\n")
-  while #lines > 0 do
-    table.insert(self.lineBuffer, lines[1])
-    table.remove(lines, 1)
-    if #lines > 0 then--      local line = table.concat(self.lineBuffer):gsub("\r$", "")
-      self.lineBuffer = {}
-      self:emit("line", line)
+  -- Handle line buffer if we have any 'line' event handlers set
+  if self.events["line"] then
+    local lines = split(data, "\n")
+    while #lines > 0 do
+      table.insert(self.lineBuffer, lines[1])
+      table.remove(lines, 1)
+      if #lines > 0 then
+        local line = table.concat(self.lineBuffer):gsub("\r$", "")
+        self.lineBuffer = {}
+        self:emit("line", line+      end
	     end

                   end
                       end

