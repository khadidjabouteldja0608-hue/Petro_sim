import pandas as pd
import matplotlib.pyplot as plt

class PetroChemicalSimulator:
    def __init__(self, sample_name, density, pressure):
        self.sample_name = sample_name
        self.density = density  # Density in g/cm3
        self.pressure = pressure  # Pressure in atm

    def calculate_viscosity_index(self):
        # حساب مؤشر اللزوجة كنموذج رياضي
        index = (self.density * 10) + (self.pressure * 0.5)
        return round(index, 2)

    def generate_data_report(self):
        # استخدام أداة Pandas لترتيب البيانات
        data = {
            'Parameter': ['Density (g/cm3)', 'Pressure (atm)', 'Viscosity Index'],
            'Value': [self.density, self.pressure, self.calculate_viscosity_index()]
        }
        return pd.DataFrame(data)

    def plot_parameters(self, df):
        # استخدام أداة Matplotlib لرسم المخطط
        plt.figure(figsize=(6, 4))
        plt.bar(df['Parameter'], df['Value'], color=['#4CAF50', '#2196F3', '#FF9800'])
        plt.title(f'Petrochemical Simulation: {self.sample_name}')
        plt.ylabel('Scale Value')
        plt.savefig('simulation_output.png')
        plt.close()

if __name__ == "__main__":
    sim = PetroChemicalSimulator("Ethylene Sample", 0.882, 12.5)
    df_report = sim.generate_data_report()
    print(df_report)
    sim.plot_parameters(df_report)

