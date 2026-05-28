from petro_sim import PetroChemicalSimulator

def test_viscosity_index():
    test_sim = PetroChemicalSimulator("Test Sample", 0.8, 10.0)
    assert test_sim.calculate_viscosity_index() == 13.0

