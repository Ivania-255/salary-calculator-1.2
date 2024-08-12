from tkinter import *
from tkinter.ttk import Notebook, Progressbar
from time import *
from Settings import Settings
import sys


class App:
	def __init__(self):
		self.root = None
		self.tk = None
		self.tabs_control = None
		self.tab1 = None
		self.tab2 = None
		self.tab3 = None
		self.tab4 = None
		self.pb = None
		self.p = None
		self.sb = None
		self.salary_lbl_frame = None
		self.salary_input = None
		self.month = 0
		self.day = self.month // 30
		self.year = self.month * 12
		self.week = self.day * 7
		self.send_res = None
		self.year_res = Label()
		self.month_res = Label()
		self.week_res = Label()
		self.day_res = Label()
		self.res1 = f"yearly salary is\t{self.year}"
		self.res2 = f"monthly salary is\t{self.month}"
		self.res4 = f"weekly salary is\t{self.week}"
		self.res3 = f"daily salary is\t{self.day}"
		self.results = None
		self.res_control = True
		self.month_res.pack()
		self.year_res.pack()
		self.week_res.pack()
		self.day_res.pack()

		self.label = True

		self.set = Settings()

		self.check_theem = None
		self.enabled = IntVar()

		self.check_theem_lbl = None

		self.error = None

	def checkbutton_changed(self):
		self.enabled = IntVar()
		if self.enabled.get() == 1:
			self.check_theem_lbl = Label(self.tab3, text="swich theme to dark")
			self.check_theem_lbl.update_idletasks()
		else:
			self.check_theem_lbl = Label(self.tab3, text='swich theme to light')
			self.check_theem_lbl.update_idletasks()

	def block_of_code(self):

		# setup Notebook

		self.tabs_control = Notebook(self.tk, padding=(20,))
		self.tabs_control.enable_traversal()

		self.tab1 = Frame(self.tabs_control, bg=self.set.thems['light']["tab_color"])
		self.tab2 = Frame(self.tabs_control, bg=self.set.thems['light']["tab_color"])
		self.tab3 = Frame(self.tabs_control, bg=self.set.thems['light']["tab_color"])
		self.tab4 = Frame(self.tabs_control, bg=self.set.thems['light']["tab_color"])

		self.tabs_control.add(self.tab1, text='Input', underline=0)
		self.tabs_control.add(self.tab2, text='Output', underline=0)
		self.tabs_control.add(self.tab3, text="Settings", underline=0)
		self.tabs_control.add(self.tab4, text="About me", underline=0)

		self.tabs_control.select(self.tab1)

	# something for widgets

	def setup_win(self):
		self.tk.title('Salary calculator 1.6')
		self.tk.geometry('500x500+720+225')
		self.tk.resizable(False, False)

	def widgets(self):
		# title
		title = Label(
			self.tk,
			text='                              salary calculator                              ',
			bg='black',
			fg='white',
			font='Arial 20 bold')

		title.place(rely=0.0399, relx=0.5, anchor=CENTER)

		# Notebook widgets

		self.tabs_control.pack(pady=20, fill=BOTH, expand=True)

		# first tab

		self.salary_lbl_frame = LabelFrame(self.tab1, text='write here your monthly salary',
		                                   padx=20,
		                                   pady=20,
		                                   font="Arial 12 bold",
		                                   highlightthickness=0,
		                                   bg=self.set.thems['light']['lbl-frame_color'])
		self.salary_input = Entry(self.salary_lbl_frame, bg=self.set.thems['light']["etr_color"])
		self.send_res = Button(
			self.salary_lbl_frame,
			text="send",
			command=self.send_results,
			padx=45,
			bg=self.set.thems['light']['send-btn_color'],

		)

		self.salary_lbl_frame.pack(pady=30)
		self.salary_input.pack()
		self.send_res.pack()

		# second tab

		self.results = Label(
			self.tab2,
			text='                                                                        results                    '
			     '                                                    ',
			bg='black', fg='white')

		# third tab

		self.check_theem = Checkbutton(self.tab3, text='swich theem', variable=self.enabled,
		                               command=self.checkbutton_changed)
		self.check_theem.pack()

		self.check_theem_lbl = Label(self.tab3)
		self.check_theem_lbl.pack()

	def send_results(self):

		try:
			self.error = Label(self.tab1, text='Invalid syntax', fg="red", bg='black', font='Arial 15 bold')
			self.error.destroy()
			self.month = float(self.salary_input.get())
			self.year = self.month * 12
			self.day = self.month // 30
			self.week = self.day * 7

			self.res2 = f"monthly salary is\t{self.month}"
			self.res1 = f" yearly salary is\t{self.year}"
			self.res3 = f"weekly salary is\t{self.week}"
			self.res4 = f"daily salary is\t{self.day}"

			self.month_res = Label(self.tab2, text=self.res2, font='Arial 14 bold',
			                       bg=self.set.thems['light']['output_color'])
			self.year_res = Label(self.tab2, text=self.res1, font='Arial 14 bold',
			                      bg=self.set.thems['light']['output_color'])
			self.week_res = Label(self.tab2, text=self.res3, font='Arial 14 bold',
			                      bg=self.set.thems['light']['output_color'])
			self.day_res = Label(self.tab2, text=self.res4, font='Arial 14 bold',
			                     bg=self.set.thems['light']["output_color"])

			self.results.pack()

			if not self.salary_input.get() == "":
				if self.label:
					self.month_res.pack()
					self.year_res.pack()
					self.week_res.pack()
					self.day_res.pack()
					self.label = False
				else:
					self.month_res['text'] = ''
					self.year_res['text'] = ''
					self.week_res['text'] = ''
					self.day_res['text'] = ''

					self.month_res = Label(self.tab2, text=self.res2, font='Arial 14 bold',
					                       bg=self.set.thems['light']["output_color"])
					self.year_res = Label(self.tab2, text=self.res1, font='Arial 14 bold',
					                      bg=self.set.thems['light']["output_color"])
					self.week_res = Label(self.tab2, text=self.res3, font='Arial 14 bold',
					                      bg=self.set.thems['light']["output_color"])
					self.day_res = Label(self.tab2, text=self.res4, font='Arial 14 bold',
					                     bg=self.set.thems['light']["output_color"])

					self.month_res.pack()
					self.year_res.pack()
					self.week_res.pack()
					self.day_res.pack()
		except:
			self.error.destroy()
			self.error = Label(self.tab1, text='Invalid syntax', fg="red", bg='black', font='Arial 15 bold')
			if self.error:
				self.error.pack()
				self.error.update()
			else:
				self.error.pack()

	def open(self):
		self.root = Tk()

		self.root.geometry("+820+400")

		Label(self.root, text='Loading', font="Arial 15 bold").pack()

		self.month_res.pack()
		self.year_res.pack()
		self.week_res.pack()
		self.day_res.pack()

		self.pb = Progressbar(self.root, orient=HORIZONTAL, mode="determinate", length=400)

		self.pb.pack(pady=20)

		for i in range(101):
			self.pb.configure(value=i)
			self.pb.update()
			sleep(0.005)
		self.root.destroy()

	def exit(self):
		self.root.destroy()
		self.tk.destroy()
		sys.exit()

	def run(self):
		self.open()
		self.tk = Tk()
		self.block_of_code()
		self.setup_win()
		self.widgets()
		self.tk.mainloop()
		self.exit()


app = App()
app.run()
