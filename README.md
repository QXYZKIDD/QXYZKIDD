-- Gui to Lua
-- Version: 3.2

-- Instances:

local SSexecutor = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Frame_2 = Instance.new("Frame")
local Holder = Instance.new("TextBox")
local Execute = Instance.new("TextButton")
local Clear = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")

--Properties:

SSexecutor.Name = "SS executor"
SSexecutor.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
SSexecutor.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = SSexecutor
Frame.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
Frame.BorderColor3 = Color3.fromRGB(81, 0, 0)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.0756718516, 0, 0.605527639, 0)
Frame.Size = UDim2.new(0, 371, 0, 232)

Frame_2.Parent = Frame
Frame_2.BackgroundColor3 = Color3.fromRGB(255, 255, 0)
Frame_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
Frame_2.BorderSizePixel = 0
Frame_2.Size = UDim2.new(0, 371, 0, 16)

Holder.Name = "Holder"
Holder.Parent = Frame
Holder.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
Holder.BorderColor3 = Color3.fromRGB(255, 255, 0)
Holder.BorderSizePixel = 0
Holder.Position = UDim2.new(0.0377358496, 0, 0.267241389, 0)
Holder.Size = UDim2.new(0, 342, 0, 119)
Holder.Font = Enum.Font.SourceSans
Holder.Text = ""
Holder.TextColor3 = Color3.fromRGB(255, 255, 255)
Holder.TextScaled = true
Holder.TextSize = 14.000
Holder.TextWrapped = true

Execute.Name = "Execute"
Execute.Parent = Frame
Execute.BackgroundColor3 = Color3.fromRGB(255, 255, 0)
Execute.BorderColor3 = Color3.fromRGB(0, 0, 0)
Execute.BorderSizePixel = 2
Execute.Position = UDim2.new(0.0673854426, 0, 0.831896544, 0)
Execute.Size = UDim2.new(0, 146, 0, 30)
Execute.Font = Enum.Font.Unknown
Execute.Text = "Execute"
Execute.TextColor3 = Color3.fromRGB(0, 0, 0)
Execute.TextScaled = true
Execute.TextSize = 14.000
Execute.TextWrapped = true

Clear.Name = "Clear"
Clear.Parent = Frame
Clear.BackgroundColor3 = Color3.fromRGB(255, 255, 0)
Clear.BorderColor3 = Color3.fromRGB(0, 0, 0)
Clear.BorderSizePixel = 2
Clear.Position = UDim2.new(0.53908354, 0, 0.831896544, 0)
Clear.Size = UDim2.new(0, 146, 0, 30)
Clear.Font = Enum.Font.Unknown
Clear.Text = "Clear"
Clear.TextColor3 = Color3.fromRGB(0, 0, 0)
Clear.TextScaled = true
Clear.TextSize = 14.000
Clear.TextWrapped = true

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.BorderSizePixel = 0
TextLabel.Position = UDim2.new(0.0377358496, 0, 0.0517241396, 0)
TextLabel.Size = UDim2.new(0, 199, 0, 50)
TextLabel.Font = Enum.Font.SourceSansBold
TextLabel.Text = "SS Executor"
TextLabel.TextColor3 = Color3.fromRGB(250, 250, 250)
TextLabel.TextScaled = true
TextLabel.TextSize = 14.000
TextLabel.TextWrapped = true

-- Module Scripts:

local fake_module_scripts = {}

do -- nil.Loadstring
	local script = Instance.new('ModuleScript', nil)
	script.Name = "Loadstring"
	local function module_script()
		--[[
				For support or to check out our other projects, join us on the Bleu Pigs Discord:
				https://discord.gg/H73NsjfBbP
				---------------
				vLua 5.1 - Lua written in Lua Virtual Machine
				---------------
				vLua is a virtual machine and compiler for dynamically compiling and executing Lua.
				It'll work on both client and server, regardless of LoadStringEnabled. This module is
				designed to be a drop in replacement for loadstring, meaning you can do the following:
				
				Example:
					local loadstring = require(workspace.Loadstring)
					local executable, compileFailReason = loadstring("print('hello from vLua!')")
					executable()
				
				Please note, vLua IS SLOWER COMPARED TO vanilla Lua, although Luau does improve performance.
				Do not attempt to run performance intensive tasks without testing first, otherwise you
				may have a bad time.
				
				Changelog:
					[8/13/2022]
						- updated FiOne to latest release - https://github.com/Rerumu/FiOne/commit/b983f11a0a318dae6c7804161b1cbc3aa52a8236
						- removed link to Minecraft server Discord
						- added link to Bleu Pigs General Discord
					[1/18/2022]
						- updated FiOne to latest release - https://github.com/Rerumu/FiOne/commit/900413a8491a44daa7770d799c85ad6df8610eea
						- added link to Minecraft server Discord
					[1/1/2022]
						- fixed environment not being properly set for compiled function
					[11/12/2021]
						- removed previous changelogs
						- updated FiOne to latest release - https://github.com/Rerumu/FiOne/blob/f443116e947e5bb3fe8bb7e6abca78214a245145/source.lua
						- fixed attempt to call a nil value error
				
				Credits:
					- FiOne LBI (created by same author as Rerubi) - https://github.com/Rerumu/FiOne
					- Yueliang 5 (Lua compiler in Lua) - http://yueliang.luaforge.net/
					- Moonshine (improved version of Yeuliang) - https://github.com/gamesys/moonshine
		]]
		local compile = require(script:WaitForChild("Yueliang"))
		local createExecutable = require(script:WaitForChild("FiOne"))
		getfenv().script = nil
		
		return function(source, env)
			local executable
			local env = env or getfenv(2)
			local name = (env.script and env.script:GetFullName())
			local ran, failureReason = pcall(function()
				local compiledBytecode = compile(source, name)
				executable = createExecutable(compiledBytecode, env)
			end)
			
			if ran then
				return setfenv(executable, env)
			end
			return nil, failureReason
		end
	end
	fake_module_scripts[script] = module_script
end
do -- nil.FiOne
	local script = Instance.new('ModuleScript', nil)
	script.Name = "FiOne"
	local function module_script()
		--[[
		FiOne
		Copyright (C) 2021  Rerumu
		
		This program is free software: you can redistribute it and/or modify
		it under the terms of the GNU General Public License as published by
		the Free Software Foundation, either version 3 of the License, or
		(at your option) any later version.
		
		This program is distributed in the hope that it will be useful,
		but WITHOUT ANY WARRANTY; without even the implied warranty of
		MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
		GNU General Public License for more details.
		
		You should have received a copy of the GNU General Public License
		along with this program.  If not, see <http://www.gnu.org/licenses/>.
		]] --
		local bit = bit or bit32 or require('bit')
		
		if not table.create then function table.create(_) return {} end end
		
		if not table.unpack then table.unpack = unpack end
		
		if not table.pack then function table.pack(...) return {n = select('#', ...), ...} end end
		
		if not table.move then
			function table.move(src, first, last, offset, dst)
				for i = 0, last - first do dst[offset + i] = src[first + i] end
			end
		end
		
		local lua_bc_to_state
		local lua_wrap_state
		local stm_lua_func
		
		-- SETLIST config
		local FIELDS_PER_FLUSH = 50
		
		-- remap for better lookup
		local OPCODE_RM = {
			-- level 1
			[22] = 18, -- JMP
			[31] = 8, -- FORLOOP
			[33] = 28, -- TFORLOOP
			-- level 2
			[0] = 3, -- MOVE
			[1] = 13, -- LOADK
			[2] = 23, -- LOADBOOL
			[26] = 33, -- TEST
			-- level 3
			[12] = 1, -- ADD
			[13] = 6, -- SUB
			[14] = 10, -- MUL
			[15] = 16, -- DIV
			[16] = 20, -- MOD
			[17] = 26, -- POW
			[18] = 30, -- UNM
			[19] = 36, -- NOT
			-- level 4
			[3] = 0, -- LOADNIL
			[4] = 2, -- GETUPVAL
			[5] = 4, -- GETGLOBAL
			[6] = 7, -- GETTABLE
			[7] = 9, -- SETGLOBAL
			[8] = 12, -- SETUPVAL
			[9] = 14, -- SETTABLE
			[10] = 17, -- NEWTABLE
			[20] = 19, -- LEN
			[21] = 22, -- CONCAT
			[23] = 24, -- EQ
			[24] = 27, -- LT
			[25] = 29, -- LE
			[27] = 32, -- TESTSET
			[32] = 34, -- FORPREP
			[34] = 37, -- SETLIST
			-- level 5
			[11] = 5, -- SELF
			[28] = 11, -- CALL
			[29] = 15, -- TAILCALL
			[30] = 21, -- RETURN
			[35] = 25, -- CLOSE
			[36] = 31, -- CLOSURE
			[37] = 35, -- VARARG
		}
		
		-- opcode types for getting values
		local OPCODE_T = {
			[0] = 'ABC',
			'ABx',
			'ABC',
			'ABC',
			'ABC',
			'ABx',
			'ABC',
			'ABx',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'AsBx',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'ABC',
			'AsBx',
			'AsBx',
			'ABC',
			'ABC',
			'ABC',
			'ABx',
			'ABC',
		}
		
		local OPCODE_M = {
			[0] = {b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgK', c = 'OpArgN'},
			{b = 'OpArgU', c = 'OpArgU'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgU', c = 'OpArgN'},
			{b = 'OpArgK', c = 'OpArgN'},
			{b = 'OpArgR', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgN'},
			{b = 'OpArgU', c = 'OpArgN'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgU', c = 'OpArgU'},
			{b = 'OpArgR', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgR', c = 'OpArgR'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgK', c = 'OpArgK'},
			{b = 'OpArgR', c = 'OpArgU'},
			{b = 'OpArgR', c = 'OpArgU'},
			{b = 'OpArgU', c = 'OpArgU'},
			{b = 'OpArgU', c = 'OpArgU'},
			{b = 'OpArgU', c = 'OpArgN'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgR', c = 'OpArgN'},
			{b = 'OpArgN', c = 'OpArgU'},
			{b = 'OpArgU', c = 'OpArgU'},
			{b = 'OpArgN', c = 'OpArgN'},
			{b = 'OpArgU', c = 'OpArgN'},
			{b = 'OpArgU', c = 'OpArgN'},
		}
		
		-- int rd_int_basic(string src, int s, int e, int d)
		-- @src - Source binary string
		-- @s - Start index of a little endian integer
		-- @e - End index of the integer
		-- @d - Direction of the loop
		local function rd_int_basic(src, s, e, d)
			local num = 0
		
			-- if bb[l] > 127 then -- signed negative
			-- 	num = num - 256 ^ l
			-- 	bb[l] = bb[l] - 128
			-- end
		
			for i = s, e, d do
				local mul = 256 ^ math.abs(i - s)
		
				num = num + mul * string.byte(src, i, i)
			end
		
			return num
		end
		
		-- float rd_flt_basic(byte f1..8)
		-- @f1..4 - The 4 bytes composing a little endian float
		local function rd_flt_basic(f1, f2, f3, f4)
			local sign = (-1) ^ bit.rshift(f4, 7)
			local exp = bit.rshift(f3, 7) + bit.lshift(bit.band(f4, 0x7F), 1)
			local frac = f1 + bit.lshift(f2, 8) + bit.lshift(bit.band(f3, 0x7F), 16)
			local normal = 1
		
			if exp == 0 then
				if frac == 0 then
					return sign * 0
				else
					normal = 0
					exp = 1
				end
			elseif exp == 0x7F then
				if frac == 0 then
					return sign * (1 / 0)
				else
					return sign * (0 / 0)
				end
			end
		
			return sign * 2 ^ (exp - 127) * (1 + normal / 2 ^ 23)
		end
		
		-- double rd_dbl_basic(byte f1..8)
		-- @f1..8 - The 8 bytes composing a little endian double
		local function rd_dbl_basic(f1, f2, f3, f4, f5, f6, f7, f8)
			local sign = (-1) ^ bit.rshift(f8, 7)
			local exp = bit.lshift(bit.band(f8, 0x7F), 4) + bit.rshift(f7, 4)
			local frac = bit.band(f7, 0x0F) * 2 ^ 48
			local normal = 1
		
			frac = frac + (f6 * 2 ^ 40) + (f5 * 2 ^ 32) + (f4 * 2 ^ 24) + (f3 * 2 ^ 16) + (f2 * 2 ^ 8) + f1 -- help
		
			if exp == 0 then
				if frac == 0 then
					return sign * 0
				else
					normal = 0
					exp = 1
				end
			elseif exp == 0x7FF then
				if frac == 0 then
					return sign * (1 / 0)
				else
					return sign * (0 / 0)
				end
			end
		
			return sign * 2 ^ (exp - 1023) * (normal + frac / 2 ^ 52)
		end
		
		-- int rd_int_le(string src, int s, int e)
		-- @src - Source binary string
		-- @s - Start index of a little endian integer
		-- @e - End index of the integer
		local function rd_int_le(src, s, e) return rd_int_basic(src, s, e - 1, 1) end
		
		-- int rd_int_be(string src, int s, int e)
		-- @src - Source binary string
		-- @s - Start index of a big endian integer
		-- @e - End index of the integer
		local function rd_int_be(src, s, e) return rd_int_basic(src, e - 1, s, -1) end
		
		-- float rd_flt_le(string src, int s)
		-- @src - Source binary string
		-- @s - Start index of little endian float
		local function rd_flt_le(src, s) return rd_flt_basic(string.byte(src, s, s + 3)) end
		
		-- float rd_flt_be(string src, int s)
		-- @src - Source binary string
		-- @s - Start index of big endian float
		local function rd_flt_be(src, s)
			local f1, f2, f3, f4 = string.byte(src, s, s + 3)
			return rd_flt_basic(f4, f3, f2, f1)
		end
		
		-- double rd_dbl_le(string src, int s)
		-- @src - Source binary string
		-- @s - Start index of little endian double
		local function rd_dbl_le(src, s) return rd_dbl_basic(string.byte(src, s, s + 7)) end
		
		-- double rd_dbl_be(string src, int s)
		-- @src - Source binary string
		-- @s - Start index of big endian double
		local function rd_dbl_be(src, s)
			local f1, f2, f3, f4, f5, f6, f7, f8 = string.byte(src, s, s + 7) -- same
			return rd_dbl_basic(f8, f7, f6, f5, f4, f3, f2, f1)
		end
		
		-- to avoid nested ifs in deserializing
		local float_types = {
			[4] = {little = rd_flt_le, big = rd_flt_be},
			[8] = {little = rd_dbl_le, big = rd_dbl_be},
		}
		
		-- byte stm_byte(Stream S)
		-- @S - Stream object to read from
		local function stm_byte(S)
			local idx = S.index
			local bt = string.byte(S.source, idx, idx)
		
			S.index = idx + 1
			return bt
		end
		
		-- string stm_string(Stream S, int len)
		-- @S - Stream object to read from
		-- @len - Length of string being read
		local function stm_string(S, len)
			local pos = S.index + len
			local str = string.sub(S.source, S.index, pos - 1)
		
			S.index = pos
			return str
		end
		
		-- string stm_lstring(Stream S)
		-- @S - Stream object to read from
		local function stm_lstring(S)
			local len = S:s_szt()
			local str
		
			if len ~= 0 then str = string.sub(stm_string(S, len), 1, -2) end
		
			return str
		end
		
		-- fn cst_int_rdr(string src, int len, fn func)
		-- @len - Length of type for reader
		-- @func - Reader callback
		local function cst_int_rdr(len, func)
			return function(S)
				local pos = S.index + len
				local int = func(S.source, S.index, pos)
				S.index = pos
		
				return int
			end
		end
		
		-- fn cst_flt_rdr(string src, int len, fn func)
		-- @len - Length of type for reader
		-- @func - Reader callback
		local function cst_flt_rdr(len, func)
			return function(S)
				local flt = func(S.source, S.index)
				S.index = S.index + len
		
				return flt
			end
		end
		
		local function stm_inst_list(S)
			local len = S:s_int()
			local list = table.create(len)
		
			for i = 1, len do
				local ins = S:s_ins()
				local op = bit.band(ins, 0x3F)
				local args = OPCODE_T[op]
				local mode = OPCODE_M[op]
				local data = {value = ins, op = OPCODE_RM[op], A = bit.band(bit.rshift(ins, 6), 0xFF)}
		
				if args == 'ABC' then
					data.B = bit.band(bit.rshift(ins, 23), 0x1FF)
					data.C = bit.band(bit.rshift(ins, 14), 0x1FF)
					data.is_KB = mode.b == 'OpArgK' and data.B > 0xFF -- post process optimization
					data.is_KC = mode.c == 'OpArgK' and data.C > 0xFF
				elseif args == 'ABx' then
					data.Bx = bit.band(bit.rshift(ins, 14), 0x3FFFF)
					data.is_K = mode.b == 'OpArgK'
				elseif args == 'AsBx' then
					data.sBx = bit.band(bit.rshift(ins, 14), 0x3FFFF) - 131071
				end
		
				list[i] = data
			end
		
			return list
		end
		
		local function stm_const_list(S)
			local len = S:s_int()
			local list = table.create(len)
		
			for i = 1, len do
				local tt = stm_byte(S)
				local k
		
				if tt == 1 then
					k = stm_byte(S) ~= 0
				elseif tt == 3 then
					k = S:s_num()
				elseif tt == 4 then
					k = stm_lstring(S)
				end
		
				list[i] = k -- offset +1 during instruction decode
			end
		
			return list
		end
		
		local function stm_sub_list(S, src)
			local len = S:s_int()
			local list = table.create(len)
		
			for i = 1, len do
				list[i] = stm_lua_func(S, src) -- offset +1 in CLOSURE
			end
		
			return list
		end
		
		local function stm_line_list(S)
			local len = S:s_int()
			local list = table.create(len)
		
			for i = 1, len do list[i] = S:s_int() end
		
			return list
		end
		
		local function stm_loc_list(S)
			local len = S:s_int()
			local list = table.create(len)
		
			for i = 1, len do list[i] = {varname = stm_lstring(S), startpc = S:s_int(), endpc = S:s_int()} end
		
			return list
		end
		
		local function stm_upval_list(S)
			local len = S:s_int()
			local list = table.create(len)
		
			for i = 1, len do list[i] = stm_lstring(S) end
		
			return list
		end
		
		function stm_lua_func(S, psrc)
			local proto = {}
			local src = stm_lstring(S) or psrc -- source is propagated
		
			proto.source = src -- source name
		
			S:s_int() -- line defined
			S:s_int() -- last line defined
		
			proto.num_upval = stm_byte(S) -- num upvalues
			proto.num_param = stm_byte(S) -- num params
		
			stm_byte(S) -- vararg flag
			proto.max_stack = stm_byte(S) -- max stack size
		
			proto.code = stm_inst_list(S)
			proto.const = stm_const_list(S)
			proto.subs = stm_sub_list(S, src)
			proto.lines = stm_line_list(S)
		
			stm_loc_list(S)
			stm_upval_list(S)
		
			-- post process optimization
			for _, v in ipairs(proto.code) do
				if v.is_K then
					v.const = proto.const[v.Bx + 1] -- offset for 1 based index
				else
					if v.is_KB then v.const_B = proto.const[v.B - 0xFF] end
		
					if v.is_KC then v.const_C = proto.const[v.C - 0xFF] end
				end
			end
		
			return proto
		end
		
		function lua_bc_to_state(src)
			-- func reader
			local rdr_func
		
			-- header flags
			local little
			local size_int
			local size_szt
			local size_ins
			local size_num
			local flag_int
		
			-- stream object
			local stream = {
				-- data
				index = 1,
				source = src,
			}
		
			assert(stm_string(stream, 4) == '\27Lua', 'invalid Lua signature')
			assert(stm_byte(stream) == 0x51, 'invalid Lua version')
			assert(stm_byte(stream) == 0, 'invalid Lua format')
		
			little = stm_byte(stream) ~= 0
			size_int = stm_byte(stream)
			size_szt = stm_byte(stream)
			size_ins = stm_byte(stream)
			size_num = stm_byte(stream)
			flag_int = stm_byte(stream) ~= 0
		
			rdr_func = little and rd_int_le or rd_int_be
			stream.s_int = cst_int_rdr(size_int, rdr_func)
			stream.s_szt = cst_int_rdr(size_szt, rdr_func)
			stream.s_ins = cst_int_rdr(size_ins, rdr_func)
		
			if flag_int then
				stream.s_num = cst_int_rdr(size_num, rdr_func)
			elseif float_types[size_num] then
				stream.s_num = cst_flt_rdr(size_num, float_types[size_num][little and 'little' or 'big'])
			else
				error('unsupported float size')
			end
		
			return stm_lua_func(stream, '@virtual')
		end
		
		local function close_lua_upvalues(list, index)
			for i, uv in pairs(list) do
				if uv.index >= index then
					uv.value = uv.store[uv.index] -- store value
					uv.store = uv
					uv.index = 'value' -- self reference
					list[i] = nil
				end
			end
		end
		
		local function open_lua_upvalue(list, index, memory)
			local prev = list[index]
		
			if not prev then
				prev = {index = index, store = memory}
				list[index] = prev
			end
		
			return prev
		end
		
		local function on_lua_error(failed, err)
			local src = failed.source
			local line = failed.lines[failed.pc - 1]
		
			error(string.format('%s:%i: %s', src, line, err), 0)
		end
		
		local function run_lua_func(state, env, upvals)
			local code = state.code
			local subs = state.subs
			local vararg = state.vararg
		
			local top_index = -1
			local open_list = {}
			local memory = state.memory
			local pc = state.pc
		
			while true do
				local inst = code[pc]
				local op = inst.op
				pc = pc + 1
		
				if op < 18 then
					if op < 8 then
						if op < 3 then
							if op < 1 then
								--[[LOADNIL]]
								for i = inst.A, inst.B do memory[i] = nil end
							elseif op > 1 then
								--[[GETUPVAL]]
								local uv = upvals[inst.B]
		
								memory[inst.A] = uv.store[uv.index]
							else
								--[[ADD]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								memory[inst.A] = lhs + rhs
							end
						elseif op > 3 then
							if op < 6 then
								if op > 4 then
									--[[SELF]]
									local A = inst.A
									local B = inst.B
									local index
		
									if inst.is_KC then
										index = inst.const_C
									else
										index = memory[inst.C]
									end
		
									memory[A + 1] = memory[B]
									memory[A] = memory[B][index]
								else
									--[[GETGLOBAL]]
									memory[inst.A] = env[inst.const]
								end
							elseif op > 6 then
								--[[GETTABLE]]
								local index
		
								if inst.is_KC then
									index = inst.const_C
								else
									index = memory[inst.C]
								end
		
								memory[inst.A] = memory[inst.B][index]
							else
								--[[SUB]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								memory[inst.A] = lhs - rhs
							end
						else --[[MOVE]]
							memory[inst.A] = memory[inst.B]
						end
					elseif op > 8 then
						if op < 13 then
							if op < 10 then
								--[[SETGLOBAL]]
								env[inst.const] = memory[inst.A]
							elseif op > 10 then
								if op < 12 then
									--[[CALL]]
									local A = inst.A
									local B = inst.B
									local C = inst.C
									local params
		
									if B == 0 then
										params = top_index - A
									else
										params = B - 1
									end
		
									local ret_list = table.pack(memory[A](table.unpack(memory, A + 1, A + params)))
									local ret_num = ret_list.n
		
									if C == 0 then
										top_index = A + ret_num - 1
									else
										ret_num = C - 1
									end
		
									table.move(ret_list, 1, ret_num, A, memory)
								else
									--[[SETUPVAL]]
									local uv = upvals[inst.B]
		
									uv.store[uv.index] = memory[inst.A]
								end
							else
								--[[MUL]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								memory[inst.A] = lhs * rhs
							end
						elseif op > 13 then
							if op < 16 then
								if op > 14 then
									--[[TAILCALL]]
									local A = inst.A
									local B = inst.B
									local params
		
									if B == 0 then
										params = top_index - A
									else
										params = B - 1
									end
		
									close_lua_upvalues(open_list, 0)
		
									return memory[A](table.unpack(memory, A + 1, A + params))
								else
									--[[SETTABLE]]
									local index, value
		
									if inst.is_KB then
										index = inst.const_B
									else
										index = memory[inst.B]
									end
		
									if inst.is_KC then
										value = inst.const_C
									else
										value = memory[inst.C]
									end
		
									memory[inst.A][index] = value
								end
							elseif op > 16 then
								--[[NEWTABLE]]
								memory[inst.A] = {}
							else
								--[[DIV]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								memory[inst.A] = lhs / rhs
							end
						else
							--[[LOADK]]
							memory[inst.A] = inst.const
						end
					else
						--[[FORLOOP]]
						local A = inst.A
						local step = memory[A + 2]
						local index = memory[A] + step
						local limit = memory[A + 1]
						local loops
		
						if step == math.abs(step) then
							loops = index <= limit
						else
							loops = index >= limit
						end
		
						if loops then
							memory[A] = index
							memory[A + 3] = index
							pc = pc + inst.sBx
						end
					end
				elseif op > 18 then
					if op < 28 then
						if op < 23 then
							if op < 20 then
								--[[LEN]]
								memory[inst.A] = #memory[inst.B]
							elseif op > 20 then
								if op < 22 then
									--[[RETURN]]
									local A = inst.A
									local B = inst.B
									local len
		
									if B == 0 then
										len = top_index - A + 1
									else
										len = B - 1
									end
		
									close_lua_upvalues(open_list, 0)
		
									return table.unpack(memory, A, A + len - 1)
								else
									--[[CONCAT]]
									local B = inst.B
									local str = memory[B]
		
									for i = B + 1, inst.C do str = str .. memory[i] end
		
									memory[inst.A] = str
								end
							else
								--[[MOD]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								memory[inst.A] = lhs % rhs
							end
						elseif op > 23 then
							if op < 26 then
								if op > 24 then
									--[[CLOSE]]
									close_lua_upvalues(open_list, inst.A)
								else
									--[[EQ]]
									local lhs, rhs
		
									if inst.is_KB then
										lhs = inst.const_B
									else
										lhs = memory[inst.B]
									end
		
									if inst.is_KC then
										rhs = inst.const_C
									else
										rhs = memory[inst.C]
									end
		
									if (lhs == rhs) == (inst.A ~= 0) then pc = pc + code[pc].sBx end
		
									pc = pc + 1
								end
							elseif op > 26 then
								--[[LT]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								if (lhs < rhs) == (inst.A ~= 0) then pc = pc + code[pc].sBx end
		
								pc = pc + 1
							else
								--[[POW]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								memory[inst.A] = lhs ^ rhs
							end
						else
							--[[LOADBOOL]]
							memory[inst.A] = inst.B ~= 0
		
							if inst.C ~= 0 then pc = pc + 1 end
						end
					elseif op > 28 then
						if op < 33 then
							if op < 30 then
								--[[LE]]
								local lhs, rhs
		
								if inst.is_KB then
									lhs = inst.const_B
								else
									lhs = memory[inst.B]
								end
		
								if inst.is_KC then
									rhs = inst.const_C
								else
									rhs = memory[inst.C]
								end
		
								if (lhs <= rhs) == (inst.A ~= 0) then pc = pc + code[pc].sBx end
		
								pc = pc + 1
							elseif op > 30 then
								if op < 32 then
									--[[CLOSURE]]
									local sub = subs[inst.Bx + 1] -- offset for 1 based index
									local nups = sub.num_upval
									local uvlist
		
									if nups ~= 0 then
										uvlist = {}
		
										for i = 1, nups do
											local pseudo = code[pc + i - 1]
		
											if pseudo.op == OPCODE_RM[0] then -- @MOVE
												uvlist[i - 1] = open_lua_upvalue(open_list, pseudo.B, memory)
											elseif pseudo.op == OPCODE_RM[4] then -- @GETUPVAL
												uvlist[i - 1] = upvals[pseudo.B]
											end
										end
		
										pc = pc + nups
									end
		
									memory[inst.A] = lua_wrap_state(sub, env, uvlist)
								else
									--[[TESTSET]]
									local A = inst.A
									local B = inst.B
		
									if (not memory[B]) ~= (inst.C ~= 0) then
										memory[A] = memory[B]
										pc = pc + code[pc].sBx
									end
									pc = pc + 1
								end
							else
								--[[UNM]]
								memory[inst.A] = -memory[inst.B]
							end
						elseif op > 33 then
							if op < 36 then
								if op > 34 then
									--[[VARARG]]
									local A = inst.A
									local len = inst.B
		
									if len == 0 then
										len = vararg.len
										top_index = A + len - 1
									end
		
									table.move(vararg.list, 1, len, A, memory)
								else
									--[[FORPREP]]
									local A = inst.A
									local init, limit, step
		
									init = assert(tonumber(memory[A]), 'for initial value must be a number')
									limit = assert(tonumber(memory[A + 1]), 'for limit must be a number')
									step = assert(tonumber(memory[A + 2]), 'for step must be a number')
		
									memory[A] = init - step
									memory[A + 1] = limit
									memory[A + 2] = step
		
									pc = pc + inst.sBx
								end
							elseif op > 36 then
								--[[SETLIST]]
								local A = inst.A
								local C = inst.C
								local len = inst.B
								local tab = memory[A]
								local offset
		
								if len == 0 then len = top_index - A end
		
								if C == 0 then
									C = inst[pc].value
									pc = pc + 1
								end
		
								offset = (C - 1) * FIELDS_PER_FLUSH
		
								table.move(memory, A + 1, A + len, offset + 1, tab)
							else
								--[[NOT]]
								memory[inst.A] = not memory[inst.B]
							end
						else
							--[[TEST]]
							if (not memory[inst.A]) ~= (inst.C ~= 0) then pc = pc + code[pc].sBx end
							pc = pc + 1
						end
					else
						--[[TFORLOOP]]
						local A = inst.A
						local base = A + 3
		
						local vals = {memory[A](memory[A + 1], memory[A + 2])}
		
						table.move(vals, 1, inst.C, base, memory)
		
						if memory[base] ~= nil then
							memory[A + 2] = memory[base]
							pc = pc + code[pc].sBx
						end
		
						pc = pc + 1
					end
				else
					--[[JMP]]
					pc = pc + inst.sBx
				end
		
				state.pc = pc
			end
		end
		
		function lua_wrap_state(proto, env, upval)
			local function wrapped(...)
				local passed = table.pack(...)
				local memory = table.create(proto.max_stack)
				local vararg = {len = 0, list = {}}
		
				table.move(passed, 1, proto.num_param, 0, memory)
		
				if proto.num_param < passed.n then
					local start = proto.num_param + 1
					local len = passed.n - proto.num_param
		
					vararg.len = len
					table.move(passed, start, start + len - 1, 1, vararg.list)
				end
		
				local state = {vararg = vararg, memory = memory, code = proto.code, subs = proto.subs, pc = 1}
		
				local result = table.pack(pcall(run_lua_func, state, env, upval))
		
				if result[1] then
					return table.unpack(result, 2, result.n)
				else
					local failed = {pc = state.pc, source = proto.source, lines = proto.lines}
		
					on_lua_error(failed, result[2])
		
					return
				end
			end
		
			return wrapped
		end
		
		return function(bCode, env)
			return lua_wrap_state(lua_bc_to_state(bCode), env or getfenv(0))
		end
	end
	fake_module_scripts[script] = module_script
end
do -- nil.Yueliang
	local script = Instance.new('ModuleScript', nil)
	script.Name = "Yueliang"
	local function module_script()
		-- Adapted from the amazing Yueliang project
		-- http://yueliang.luaforge.net/
		
		
		--[[--------------------------------------------------------------------
		
		luac.lua
		Primitive luac in Lua
		This file is part of Yueliang.
		
		Copyright (c) 2005-2007 Kein-Hong Man <khman@users.sf.net>
		The COPYRIGHT file describes the conditions
		under which this software may be distributed.
		
		See the ChangeLog for more information.
		
		----------------------------------------------------------------------]]
		
		--[[--------------------------------------------------------------------
		-- Notes:
		-- * based on luac.lua in the test directory of the 5.1.2 distribution
		-- * usage: lua luac.lua file.lua
		----------------------------------------------------------------------]]
		
		------------------------------------------------------------------------
		-- load and initialize the required modules
		------------------------------------------------------------------------
		local luaZ = {}
		local luaY = {}
		local luaX = {}
		local luaP = {}
		local luaU = {}
		local luaK = {}
		local size_size_t = 8
		
		
		-- currently asserts are enabled because the codebase hasn't been tested
		-- much (if you don't want asserts, just comment them out)
		local function lua_assert(test)
			if not test then error("assertion failed!") end
		end
		
		
		
		-- dofile("lzio.lua")
		
		
		------------------------------------------------------------------------
		-- * reader() should return a string, or nil if nothing else to parse.
		--   Additional data can be set only during stream initialization
		-- * Readers are handled in lauxlib.c, see luaL_load(file|buffer|string)
		-- * LUAL_BUFFERSIZE=BUFSIZ=512 in make_getF() (located in luaconf.h)
		-- * Original Reader typedef:
		--   const char * (*lua_Reader) (lua_State *L, void *ud, size_t *sz);
		-- * This Lua chunk reader implementation:
		--   returns string or nil, no arguments to function
		------------------------------------------------------------------------
		
		------------------------------------------------------------------------
		-- create a chunk reader from a source string
		------------------------------------------------------------------------
		function luaZ:make_getS(buff)
			local b = buff
			return function() -- chunk reader anonymous function here
				if not b then return nil end
				local data = b
				b = nil
				return data
			end
		end
		
		------------------------------------------------------------------------
		-- create a chunk reader from a source file
		------------------------------------------------------------------------
		-- function luaZ:make_getF(filename)
		--   local LUAL_BUFFERSIZE = 512
		--   local h = io.open(filename, "r")
		--   if not h then return nil end
		--   return function() -- chunk reader anonymous function here
		--     if not h or io.type(h) == "closed file" then return nil end
		--     local buff = h:read(LUAL_BUFFERSIZE)
		--     if not buff then h:close(); h = nil end
		--     return buff
		--   end
		-- end
		
		function luaZ:make_getF(source)
			local LUAL_BUFFERSIZE = 512
			local pos = 1
		
			return function() -- chunk reader anonymous function here
				local buff = source:sub(pos, pos + LUAL_BUFFERSIZE - 1)
				pos = math.min(#source + 1, pos + LUAL_BUFFERSIZE)
				return buff
			end
		end
		
		
		------------------------------------------------------------------------
		-- creates a zio input stream
		-- returns the ZIO structure, z
		------------------------------------------------------------------------
		function luaZ:init(reader, data)
			if not reader then return end
			local z = {}
			z.reader = reader
			z.data = data or ""
			z.name = name
			-- set up additional data for reading
			if not data or data == "" then z.n = 0 else z.n = #data end
			z.p = 0
			return z
		end
		
		------------------------------------------------------------------------
		-- fill up input buffer
		------------------------------------------------------------------------
		function luaZ:fill(z)
			local buff = z.reader()
			z.data = buff
			if not buff or buff == "" then return "EOZ" end
			z.n, z.p = #buff - 1, 1
			return string.sub(buff, 1, 1)
		end
		
		------------------------------------------------------------------------
		-- get next character from the input stream
		-- * local n, p are used to optimize code generation
		------------------------------------------------------------------------
		function luaZ:zgetc(z)
			local n, p = z.n, z.p + 1
			if n > 0 then
				z.n, z.p = n - 1, p
				return string.sub(z.data, p, p)
			else
				return self:fill(z)
			end
		end
		
		
		
		
		
		-- dofile("llex.lua")
		
		-- FIRST_RESERVED is not required as tokens are manipulated as strings
		-- TOKEN_LEN deleted; maximum length of a reserved word not needed
		
		------------------------------------------------------------------------
		-- "ORDER RESERVED" deleted; enumeration in one place: luaX.RESERVED
		------------------------------------------------------------------------
		
		-- terminal symbols denoted by reserved words: TK_AND to TK_WHILE
		-- other terminal symbols: TK_NAME to TK_EOS
		luaX.RESERVED = [[
		TK_AND and
		TK_BREAK break
		TK_DO do
		TK_ELSE else
		TK_ELSEIF elseif
		TK_END end
		TK_FALSE false
		TK_FOR for
		TK_FUNCTION function
		TK_IF if
		TK_IN in
		TK_LOCAL local
		TK_NIL nil
		TK_NOT not
		TK_OR or
		TK_REPEAT repeat
		TK_RETURN return
		TK_THEN then
		TK_TRUE true
		TK_UNTIL until
		TK_WHILE while
		TK_CONCAT ..
		TK_DOTS ...
		TK_EQ ==
		TK_GE >=
		TK_LE <=
		TK_NE ~=
		TK_NAME <name>
		TK_NUMBER <number>
		TK_STRING <string>
		TK_EOS <eof>]]
		
		-- NUM_RESERVED is not required; number of reserved words
		
		--[[--------------------------------------------------------------------
		-- Instead of passing seminfo, the Token struct (e.g. ls.t) is passed
		-- so that lexer functions can use its table element, ls.t.seminfo
		--
		-- SemInfo (struct no longer needed, a mixed-type value is used)
		--
		-- Token (struct of ls.t and ls.lookahead):
		--   token  -- token symbol
		--   seminfo  -- semantics information
		--
		-- LexState (struct of ls; ls is initialized by luaX:setinput):
		--   current  -- current character (charint)
		--   linenumber  -- input line counter
		--   lastline  -- line of last token 'consumed'
		--   t  -- current token (table: struct Token)
		--   lookahead  -- look ahead token (table: struct Token)
		--   fs  -- 'FuncState' is private to the parser
		--   L -- LuaState
		--   z  -- input stream
		--   buff  -- buffer for tokens
		--   source  -- current source name
		--   decpoint -- locale decimal point
		--   nestlevel  -- level of nested non-terminals
		----------------------------------------------------------------------]]
		
		-- luaX.tokens (was luaX_tokens) is now a hash; see luaX:init
		
		luaX.MAXSRC = 80
		luaX.MAX_INT = 2147483645       -- constants from elsewhere (see above)
		luaX.LUA_QS = "'%s'"
		luaX.LUA_COMPAT_LSTR = 1
		--luaX.MAX_SIZET = 4294967293
		
		------------------------------------------------------------------------
		-- initialize lexer
		-- * original luaX_init has code to create and register token strings
		-- * luaX.tokens: TK_* -> token
		-- * luaX.enums:  token -> TK_* (used in luaX:llex)
		------------------------------------------------------------------------
		function luaX:init()
			local tokens, enums = {}, {}
			for v in string.gmatch(self.RESERVED, "[^\n]+") do
				local _, _, tok, str = string.find(v, "(%S+)%s+(%S+)")
				tokens[tok] = str
				enums[str] = tok
			end
			self.tokens = tokens
			self.enums = enums
		end
		
		------------------------------------------------------------------------
		-- returns a suitably-formatted chunk name or id
		-- * from lobject.c, used in llex.c and ldebug.c
		-- * the result, out, is returned (was first argument)
		------------------------------------------------------------------------
		function luaX:chunkid(source, bufflen)
			local out
			local first = string.sub(source, 1, 1)
			if first == "=" then
				out = string.sub(source, 2, bufflen)  -- remove first char
			else  -- out = "source", or "...source"
				if first == "@" then
					source = string.sub(source, 2)  -- skip the '@'
					bufflen = bufflen - #" '...' "
					local l = #source
					out = ""
					if l > bufflen then
						source = string.sub(source, 1 + l - bufflen)  -- get last part of file name
						out = out.."..."
					end
					out = out..source
				else  -- out = [string "string"]
					local len = string.find(source, "[\n\r]")  -- stop at first newline
					len = len and (len - 1) or #source
					bufflen = bufflen - #(" [string \"...\"] ")
					if len > bufflen then len = bufflen end
					out = "[string \""
					if len < #source then  -- must truncate?
						out = out..string.sub(source, 1, len).."..."
					else
						out = out..source
					end
					out = out.."\"]"
				end
			end
			return out
		end
		
		--[[--------------------------------------------------------------------
		-- Support functions for lexer
		-- * all lexer errors eventually reaches lexerror:
				 syntaxerror -> lexerror
		----------------------------------------------------------------------]]
		
		------------------------------------------------------------------------
		-- look up token and return keyword if found (also called by parser)
		------------------------------------------------------------------------
		function luaX:token2str(ls, token)
			if string.sub(token, 1, 3) ~= "TK_" then
				if string.find(token, "%c") then
					return string.format("char(%d)", string.byte(token))
				end
				return token
			else
				return self.tokens[token]
			end
		end
		
		------------------------------------------------------------------------
		-- throws a lexer error
		-- * txtToken has been made local to luaX:lexerror
		-- * can't communicate LUA_ERRSYNTAX, so it is unimplemented
		------------------------------------------------------------------------
		function luaX:lexerror(ls, msg, token)
			local function txtToken(ls, token)
				if token == "TK_NAME" or
					token == "TK_STRING" or
					token == "TK_NUMBER" then
					return ls.buff
				else
					return self:token2str(ls, token)
				end
			end
			local buff = self:chunkid(ls.source, self.MAXSRC)
			local msg = string.format("%s:%d: %s", buff, ls.linenumber, msg)
			if token then
				msg = string.format("%s near "..self.LUA_QS, msg, txtToken(ls, token))
			end
			-- luaD_throw(ls->L, LUA_ERRSYNTAX)
			error(msg)
		end
		
		------------------------------------------------------------------------
		-- throws a syntax error (mainly called by parser)
		-- * ls.t.token has to be set by the function calling luaX:llex
		--   (see luaX:next and luaX:lookahead elsewhere in this file)
		------------------------------------------------------------------------
		function luaX:syntaxerror(ls, msg)
			self:lexerror(ls, msg, ls.t.token)
		end
		
		------------------------------------------------------------------------
		-- move on to next line
		------------------------------------------------------------------------
		function luaX:currIsNewline(ls)
			return ls.current == "\n" or ls.current == "\r"
		end
		
		function luaX:inclinenumber(ls)
			local old = ls.current
			-- lua_assert(currIsNewline(ls))
			self:nextc(ls)  -- skip '\n' or '\r'
			if self:currIsNewline(ls) and ls.current ~= old then
				self:nextc(ls)  -- skip '\n\r' or '\r\n'
			end
			ls.linenumber = ls.linenumber + 1
			if ls.linenumber >= self.MAX_INT then
				self:syntaxerror(ls, "chunk has too many lines")
			end
		end
		
		------------------------------------------------------------------------
		-- initializes an input stream for lexing
		-- * if ls (the lexer state) is passed as a table, then it is filled in,
		--   otherwise it has to be retrieved as a return value
		-- * LUA_MINBUFFER not used; buffer handling not required any more
		------------------------------------------------------------------------
		function luaX:setinput(L, ls, z, source)
			if not ls then ls = {} end  -- create struct
			if not ls.lookahead then ls.lookahead = {} end
			if not ls.t then ls.t = {} end
			ls.decpoint = "."
			ls.L = L
			ls.lookahead.token = "TK_EOS"  -- no look-ahead token
			ls.z = z
			ls.fs = nil
			ls.linenumber = 1
			ls.lastline = 1
			ls.source = source
			self:nextc(ls)  -- read first char
		end
		
		--[[--------------------------------------------------------------------
		-- LEXICAL ANALYZER
		----------------------------------------------------------------------]]
		
		------------------------------------------------------------------------
		-- checks if current character read is found in the set 'set'
		------------------------------------------------------------------------
		function luaX:check_next(ls, set)
			if not string.find(set, ls.current, 1, 1) then
				return false
			end
			self:save_and_next(ls)
			return true
		end
		
		------------------------------------------------------------------------
		-- retrieve next token, checking the lookahead buffer if necessary
		-- * note that the macro next(ls) in llex.c is now luaX:nextc
		-- * utilized used in lparser.c (various places)
		------------------------------------------------------------------------
		function luaX:next(ls)
			ls.lastline = ls.linenumber
			if ls.lookahead.token ~= "TK_EOS" then  -- is there a look-ahead token?
				-- this must be copy-by-value
				ls.t.seminfo = ls.lookahead.seminfo  -- use this one
				ls.t.token = ls.lookahead.token
				ls.lookahead.token = "TK_EOS"  -- and discharge it
			else
				ls.t.token = self:llex(ls, ls.t)  -- read next token
			end
		end
		
		------------------------------------------------------------------------
		-- fill in the lookahead buffer
		-- * utilized used in lparser.c:constructor
		------------------------------------------------------------------------
		function luaX:lookahead(ls)
			-- lua_assert(ls.lookahead.token == "TK_EOS")
			ls.lookahead.token = self:llex(ls, ls.lookahead)
		end
		
		------------------------------------------------------------------------
		-- gets the next character and returns it
		-- * this is the next() macro in llex.c; see notes at the beginning
		------------------------------------------------------------------------
		function luaX:nextc(ls)
			local c = luaZ:zgetc(ls.z)
			ls.current = c
			return c
		end
		
		------------------------------------------------------------------------
		-- saves the given character into the token buffer
		-- * buffer handling code removed, not used in this implementation
		-- * test for maximum token buffer length not used, makes things faster
		------------------------------------------------------------------------
		
		function luaX:save(ls, c)
			local buff = ls.buff
			-- if you want to use this, please uncomment luaX.MAX_SIZET further up
			--if #buff > self.MAX_SIZET then
			--  self:lexerror(ls, "lexical element too long")
			--end
			ls.buff = buff..c
		end
		
		------------------------------------------------------------------------
		-- save current character into token buffer, grabs next character
		-- * like luaX:nextc, returns the character read for convenience
		------------------------------------------------------------------------
		function luaX:save_and_next(ls)
			self:save(ls, ls.current)
			return self:nextc(ls)
		end
		
		------------------------------------------------------------------------
		-- LUA_NUMBER
		-- * luaX:read_numeral is the main lexer function to read a number
		-- * luaX:str2d, luaX:buffreplace, luaX:trydecpoint are support functions
		------------------------------------------------------------------------
		
		------------------------------------------------------------------------
		-- string to number converter (was luaO_str2d from lobject.c)
		-- * returns the number, nil if fails (originally returns a boolean)
		-- * conversion function originally lua_str2number(s,p), a macro which
		--   maps to the strtod() function by default (from luaconf.h)
		------------------------------------------------------------------------
		function luaX:str2d(s)
			local result = tonumber(s)
			if result then return result end
			-- conversion failed
			if string.lower(string.sub(s, 1, 2)) == "0x" then  -- maybe an hexadecimal constant?
				result = tonumber(s, 16)
				if result then return result end  -- most common case
				-- Was: invalid trailing characters?
				-- In C, this function then skips over trailing spaces.
				-- true is returned if nothing else is found except for spaces.
				-- If there is still something else, then it returns a false.
				-- All this is not necessary using Lua's tonumber.
			end
			return nil
		end
		
		------------------------------------------------------------------------
		-- single-character replacement, for locale-aware decimal points
		------------------------------------------------------------------------
		function luaX:buffreplace(ls, from, to)
			local result, buff = "", ls.buff
			for p = 1, #buff do
				local c = string.sub(buff, p, p)
				if c == from then c = to end
				result = result..c
			end
			ls.buff = result
		end
		
		------------------------------------------------------------------------
		-- Attempt to convert a number by translating '.' decimal points to
		-- the decimal point character used by the current locale. This is not
		-- needed in Yueliang as Lua's tonumber() is already locale-aware.
		-- Instead, the code is here in case the user implements localeconv().
		------------------------------------------------------------------------
		function luaX:trydecpoint(ls, Token)
			-- format error: try to update decimal point separator
			local old = ls.decpoint
			-- translate the following to Lua if you implement localeconv():
			-- struct lconv *cv = localeconv();
			-- ls->decpoint = (cv ? cv->decimal_point[0] : '.');
			self:buffreplace(ls, old, ls.decpoint)  -- try updated decimal separator
			local seminfo = self:str2d(ls.buff)
			Token.seminfo = seminfo
			if not seminfo then
				-- format error with correct decimal point: no more options
				self:buffreplace(ls, ls.decpoint, ".")  -- undo change (for error message)
				self:lexerror(ls, "malformed number", "TK_NUMBER")
			end
		end
		
		------------------------------------------------------------------------
		-- main number conversion function
		-- * "^%w$" needed in the scan in order to detect "EOZ"
		------------------------------------------------------------------------
		function luaX:read_numeral(ls, Token)
			-- lua_assert(string.find(ls.current, "%d"))
			repeat
				self:save_and_next(ls)
			until string.find(ls.current, "%D") and ls.current ~= "."
			if self:check_next(ls, "Ee") then  -- 'E'?
				self:check_next(ls, "+-")  -- optional exponent sign
			end
			while string.find(ls.current, "^%w$") or ls.current == "_" do
				self:save_and_next(ls)
			end
			self:buffreplace(ls, ".", ls.decpoint)  -- follow locale for decimal point
			local seminfo = self:str2d(ls.buff)
			Token.seminfo = seminfo
			if not seminfo then  -- format error?
				self:trydecpoint(ls, Token) -- try to update decimal point separator
			end
		end
		
		------------------------------------------------------------------------
		-- count separators ("=") in a long string delimiter
		-- * used by luaX:read_long_string
		------------------------------------------------------------------------
		function luaX:skip_sep(ls)
			local count = 0
			local s = ls.current
			-- lua_assert(s == "[" or s == "]")
			self:save_and_next(ls)
			while ls.current == "=" do
				self:save_and_next(ls)
				count = count + 1
			end
			return (ls.current == s) and count or (-count) - 1
		end
		
		------------------------------------------------------------------------
		-- reads a long string or long comment
		------------------------------------------------------------------------
		function luaX:read_long_string(ls, Token, sep)
			local cont = 0
			self:save_and_next(ls)  -- skip 2nd '['
			if self:currIsNewline(ls) then  -- string starts with a newline?
				self:inclinenumber(ls)  -- skip it
			end
			while true do
				local c = ls.current
				if c == "EOZ" then
					self:lexerror(ls, Token and "unfinished long string" or
						"unfinished long comment", "TK_EOS")
				elseif c == "[" then
					--# compatibility code start
					if self.LUA_COMPAT_LSTR then
						if self:skip_sep(ls) == sep then
							self:save_and_next(ls)  -- skip 2nd '['
							cont = cont + 1
							--# compatibility code start
							if self.LUA_COMPAT_LSTR == 1 then
								if sep == 0 then
									self:lexerror(ls, "nesting of [[...]] is deprecated", "[")
								end
							end
							--# compatibility code end
						end
					end
					--# compatibility code end
				elseif c == "]" then
					if self:skip_sep(ls) == sep then
						self:save_and_next(ls)  -- skip 2nd ']'
						--# compatibility code start
						if self.LUA_COMPAT_LSTR and self.LUA_COMPAT_LSTR == 2 then
							cont = cont - 1
							if sep == 0 and cont >= 0 then break end
						end
						--# compatibility code end
						break
					end
				elseif self:currIsNewline(ls) then
					self:save(ls, "\n")
					self:inclinenumber(ls)
					if not Token then ls.buff = "" end -- avoid wasting space
				else  -- default
					if Token then
						self:save_and_next(ls)
					else
						self:nextc(ls)
					end
				end--if c
			end--while
			if Token then
				local p = 3 + sep
				Token.seminfo = string.sub(ls.buff, p, -p)
			end
		end
		
		------------------------------------------------------------------------
		-- reads a string
		-- * has been restructured significantly compared to the original C code
		------------------------------------------------------------------------
		
		function luaX:read_string(ls, del, Token)
			self:save_and_next(ls)
			while ls.current ~= del do
				local c = ls.current
				if c == "EOZ" then
					self:lexerror(ls, "unfinished string", "TK_EOS")
				elseif self:currIsNewline(ls) then
					self:lexerror(ls, "unfinished string", "TK_STRING")
				elseif c == "\\" then
					c = self:nextc(ls)  -- do not save the '\'
					if self:currIsNewline(ls) then  -- go through
						self:save(ls, "\n")
						self:inclinenumber(ls)
					elseif c ~= "EOZ" then -- will raise an error next loop
						-- escapes handling greatly simplified here:
						local i = string.find("abfnrtv", c, 1, 1)
						if i then
							self:save(ls, string.sub("\a\b\f\n\r\t\v", i, i))
							self:nextc(ls)
						elseif not string.find(c, "%d") then
							self:save_and_next(ls)  -- handles \\, \", \', and \?
						else  -- \xxx
							c, i = 0, 0
							repeat
								c = 10 * c + ls.current
								self:nextc(ls)
								i = i + 1
							until i >= 3 or not string.find(ls.current, "%d")
							if c > 255 then  -- UCHAR_MAX
								self:lexerror(ls, "escape sequence too large", "TK_STRING")
							end
							self:save(ls, string.char(c))
						end
					end
				else
					self:save_and_next(ls)
				end--if c
			end--while
			self:save_and_next(ls)  -- skip delimiter
			Token.seminfo = string.sub(ls.buff, 2, -2)
		end
		
		------------------------------------------------------------------------
		-- main lexer function
		------------------------------------------------------------------------
		function luaX:llex(ls, Token)
			ls.buff = ""
			while true do
				local c = ls.current
				----------------------------------------------------------------
				if self:currIsNewline(ls) then
					self:inclinenumber(ls)
					----------------------------------------------------------------
				elseif c == "-" then
					c = self:nextc(ls)
					if c ~= "-" then return "-" end
					-- else is a comment
					local sep = -1
					if self:nextc(ls) == '[' then
						sep = self:skip_sep(ls)
						ls.buff = ""  -- 'skip_sep' may dirty the buffer
					end
					if sep >= 0 then
						self:read_long_string(ls, nil, sep)  -- long comment
						ls.buff = ""
					else  -- else short comment
						while not self:currIsNewline(ls) and ls.current ~= "EOZ" do
							self:nextc(ls)
						end
					end
					----------------------------------------------------------------
				elseif c == "[" then
					local sep = self:skip_sep(ls)
					if sep >= 0 then
						self:read_long_string(ls, Token, sep)
						return "TK_STRING"
					elseif sep == -1 then
						return "["
					else
						self:lexerror(ls, "invalid long string delimiter", "TK_STRING")
					end
					----------------------------------------------------------------
				elseif c == "=" then
					c = self:nextc(ls)
					if c ~= "=" then return "="
					else self:nextc(ls); return "TK_EQ" end
					----------------------------------------------------------------
				elseif c == "<" then
					c = self:nextc(ls)
					if c ~= "=" then return "<"
					else self:nextc(ls); return "TK_LE" end
					----------------------------------------------------------------
				elseif c == ">" then
					c = self:nextc(ls)
					if c ~= "=" then return ">"
					else self:nextc(ls); return "TK_GE" end
					----------------------------------------------------------------
				elseif c == "~" then
					c = self:nextc(ls)
					if c = "=" then return ""
					else self:nextc(ls); return "TK_NE" end
					----------------------------------------------------------------
				elseif c == "\"" or c == "'" then
					self:read_string(ls, c, Token)
					return "TK_STRING"
					----------------------------------------------------------------
				elseif c == "." then
					c = self:save_and_next(ls)
					if self:check_next(ls, ".") then
						if self:check_next(ls, ".") then
							return "TK_DOTS"   -- ...
						else return "TK_CONCAT"   -- ..
						end
					elseif not string.find(c, "%d") then
						return "."
					else
						self:read_numeral(ls, Token)
						return "TK_NUMBER"
					end
					----------------------------------------------------------------
				elseif c == "EOZ" then
					return "TK_EOS"
					----------------------------------------------------------------
				else  -- default
					if string.find(c, "%s") then
						-- lua_assert(self:currIsNewline(ls))
						self:nextc(ls)
					elseif string.find(c, "%d") then
						self:read_numeral(ls, Token)
						return "TK_NUMBER"
					elseif string.find(c, "[_%a]") then
						-- identifier or reserved word
						repeat
							c = self:save_and_next(ls)
						until c == "EOZ" or not string.find(c, "[_%w]")
						local ts = ls.buff
						local tok = self.enums[ts]
						if tok then return tok end  -- reserved word?
						Token.seminfo = ts
						return "TK_NAME"
					else
						self:nextc(ls)
						return c  -- single-char tokens (+ - / ...)
					end
					----------------------------------------------------------------
				end--if c
			end--while
		end
		
		
		
		
		
		--dofile("lopcodes.lua")
		
		
		--[[
		===========================================================================
			We assume that instructions are unsigned numbers.
			All instructions have an opcode in the first 6 bits.
			Instructions can have the following fields:
						'A' : 8 bits
						'B' : 9 bits
						'C' : 9 bits
						'Bx' : 18 bits ('B' and 'C' together)
						'sBx' : signed Bx
		
			A signed argument is represented in excess K; that is, the number
			value is the unsigned value minus K. K is exactly the maximum value
			for that argument (so that -max is represented by 0, and +max is
			represented by 2*max), which is half the maximum for the corresponding
			unsigned argument.
		===========================================================================
		--]]
		
		luaP.OpMode = { iABC = 0, iABx = 1, iAsBx = 2 }  -- basic instruction format
		
		------------------------------------------------------------------------
		-- size and position of opcode arguments.
		-- * WARNING size and position is hard-coded elsewhere in this script
		------------------------------------------------------------------------
		luaP.SIZE_C  = 9
		luaP.SIZE_B  = 9
		luaP.SIZE_Bx = luaP.SIZE_C + luaP.SIZE_B
		luaP.SIZE_A  = 8
		
		luaP.SIZE_OP = 6
		
		luaP.POS_OP = 0
		luaP.POS_A  = luaP.POS_OP + luaP.SIZE_OP
		luaP.POS_C  = luaP.POS_A + luaP.SIZE_A
		luaP.POS_B  = luaP.POS_C + luaP.SIZE_C
		luaP.POS_Bx = luaP.POS_C
		
		------------------------------------------------------------------------
		-- limits for opcode arguments.
		-- we use (signed) int to manipulate most arguments,
		-- so they must fit in LUAI_BITSINT-1 bits (-1 for sign)
		------------------------------------------------------------------------
		-- removed "#if SIZE_Bx < BITS_INT-1" test, assume this script is
		-- running on a Lua VM with double or int as LUA_NUMBER
		
		luaP.MAXARG_Bx  = math.ldexp(1, luaP.SIZE_Bx) - 1
		luaP.MAXARG_sBx = math.floor(luaP.MAXARG_Bx / 2)  -- 'sBx' is signed
		
		luaP.MAXARG_A = math.ldexp(1, luaP.SIZE_A) - 1
		luaP.MAXARG_B = math.ldexp(1, luaP.SIZE_B) - 1
		luaP.MAXARG_C = math.ldexp(1, luaP.SIZE_C) - 1
		
		-- creates a mask with 'n' 1 bits at position 'p'
		-- MASK1(n,p) deleted, not required
		-- creates a mask with 'n' 0 bits at position 'p'
		-- MASK0(n,p) deleted, not required
		
		--[[--------------------------------------------------------------------
			Visual representation for reference:
		
			 31    |    |     |            0      bit position
				+-----+-----+-----+----------+
				|  B  |  C  |  A  |  Opcode  |      iABC format
				+-----+-----+-----+----------+
				-  9  -  9  -  8  -    6     -      field sizes
				+-----+-----+-----+----------+
				|   [s]Bx   |  A  |  Opcode  |      iABx | iAsBx format
				+-----+-----+-----+----------+
		
		----------------------------------------------------------------------]]
		
		------------------------------------------------------------------------
		-- the following macros help to manipulate instructions
		-- * changed to a table object representation, very clean compared to
		--   the [nightmare] alternatives of using a number or a string
		-- * Bx is a separate element from B and C, since there is never a need
		--   to split Bx in the parser or code generator
		------------------------------------------------------------------------
		
		-- these accept or return opcodes in the form of string names
		function luaP:GET_OPCODE(i) return self.ROpCode[i.OP] end
		function luaP:SET_OPCODE(i, o) i.OP = self.OpCode[o] end
		
		function luaP:GETARG_A(i) return i.A end
		function luaP:SETARG_A(i, u) i.A = u end
		
		function luaP:GETARG_B(i) return i.B end
		function luaP:SETARG_B(i, b) i.B = b end
		
		function luaP:GETARG_C(i) return i.C end
		function luaP:SETARG_C(i, b) i.C = b end
		
		function luaP:GETARG_Bx(i) return i.Bx end
		function luaP:SETARG_Bx(i, b) i.Bx = b end
		
		function luaP:GETARG_sBx(i) return i.Bx - self.MAXARG_sBx end
		function luaP:SETARG_sBx(i, b) i.Bx = b + self.MAXARG_sBx end
		
		function luaP:CREATE_ABC(o,a,b,c)
			return {OP = self.OpCode[o], A = a, B = b, C = c}
		end
		
		function luaP:CREATE_ABx(o,a,bc)
			return {OP = self.OpCode[o], A = a, Bx = bc}
		end
		
		------------------------------------------------------------------------
		-- create an instruction from a number (for OP_SETLIST)
		------------------------------------------------------------------------
		function luaP:CREATE_Inst(c)
			local o = c % 64
			c = (c - o) / 64
			local a = c % 256
			c = (c - a) / 256
			return self:CREATE_ABx(o, a, c)
		end
		
		------------------------------------------------------------------------
		-- returns a 4-char string little-endian encoded form of an instruction
		------------------------------------------------------------------------
		function luaP:Instruction(i)
			if i.Bx then
				-- change to OP/A/B/C format
				i.C = i.Bx % 512
				i.B = (i.Bx - i.C) / 512
			end
			local I = i.A * 64 + i.OP
			local c0 = I % 256
			I = i.C * 64 + (I - c0) / 256  -- 6 bits of A left
			local c1 = I % 256
			I = i.B * 128 + (I - c1) / 256  -- 7 bits of C left
			local c2 = I % 256
			local c3 = (I - c2) / 256
			return string.char(c0, c1, c2, c3)
		end
		
		------------------------------------------------------------------------
		-- decodes a 4-char little-endian string into an instruction struct
		------------------------------------------------------------------------
		function l
